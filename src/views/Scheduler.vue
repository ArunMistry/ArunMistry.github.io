<template>
	<v-dialog v-model="dialog" max-width="700px">
		<v-card class="px-5 pb-9">
			<!-- Card-title is buggy for current version, so word wrap is needed. Check if issue fixed -->
			<v-card-title
				class="justify-center display-3 font-weight-medium py-7"
				style="word-break: normal"
			>Scheduler</v-card-title>
			<v-row justify="center">
				<v-card class="mx-5 mx-sm-0" outlined flat>
					<v-date-picker
						v-model="datearray"
						first-day-of-week="1"
						multiple
						class="ma-0"
						show-current
						:min="moment().format('yyyy-MM-DD')"
						:full-width="$vuetify.breakpoint.xsOnly"
						color="blue darken-3"
					/>
				</v-card>
				<v-card flat class="px-2 pl-sm-5 pr-sm-0 mt-5 mt-sm-0" width="360px">
					<v-menu
						ref="menu"
						v-model="timemenu"
						:close-on-content-click="false"
						:return-value.sync="time"
						transition="scale-transition"
						offset-y
						max-width="290px"
						min-width="290px"
					>
						<template v-slot:activator="{ on }">
							<v-sheet class="d-flex align-center" max-width="95%">
								Time:
								<v-text-field
									v-model="time"
									class="ml-3"
									placeholder="Select Time"
									readonly
									hide-details
									outlined
									dense
									v-on="on"
								/>
							</v-sheet>
						</template>
						<v-time-picker
							v-if="timemenu"
							v-model="time"
							class="ma-0"
							ampm-in-title
							full-width
							@click:minute="$refs.menu.save(time)"
						/>
					</v-menu>
					<v-card flat class="mt-3">
						<v-card-text class="pa-1 black--text">
							Range:
							<v-row
								class="mx-0 my-1"
								style="border-style:solid;border-width: 0.1px;border-color:#ccc;border-radius:5px"
							>
								<v-card-text class="pa-0">
									<v-btn-toggle v-model="days" class="d-block mb-1" multiple mandatory>
										<v-btn
											v-for="(day, num) in ['M','T','W','T','F','S','S']"
											:key="num"
											min-width="calc(100% / 7)"
											height="40px"
											x-large
										>{{ day }}</v-btn>
									</v-btn-toggle>
								</v-card-text>
								<v-col class="d-inline-flex pt-1 mt-1 pb-0" cols="12">
									<v-sheet class="d-flex align-center mr-3">Start:</v-sheet>
									<v-menu
										v-model="startdatemenu"
										:close-on-content-click="false"
										transition="scale-transition"
										offset-y
										min-width="290px"
									>
										<template v-slot:activator="{ on }">
											<v-text-field
												:value="moment(startdate).format('MMMM Do, yyyy')"
												readonly
												dense
												outlined
												hide-details
												class="my-0 pa-0"
												v-on="on"
											/>
										</template>
										<v-date-picker
											v-model="startdate"
											first-day-of-week="1"
											class="my-0"
											:min="moment().format('yyyy-MM-DD')"
											@input="startdatemethod"
											@change="startdatemenu=false"
										/>
									</v-menu>
								</v-col>
								<v-col>
									End:
									<v-radio-group v-model="repeattype" class="my-0 pt-0" hide-details>
										<v-radio value="repeatfor">
											<span slot="label" class="black--text d-inline-flex align-center">
												Repeat for :
												<v-sheet class="d-flex align-center mt-1 ml-5" max-width="130px">
													<v-text-field
														v-model="repeatfor"
														:rules="valuerules"
														outlined
														dense
														type="number"
														hide-details
														@input="repeatformethod"
													/>
													<span class="ml-2">week(s)</span>
												</v-sheet>
											</span>
										</v-radio>
										<v-radio value="repeatuntil">
											<span slot="label" class="black--text d-inline-flex align-center">
												<span>Repeat until :</span>
												<v-menu
													v-model="enddatemenu"
													:close-on-content-click="false"
													transition="scale-transition"
													min-width="290px"
												>
													<template v-slot:activator="{ on }">
														<!-- @mousedown used because radio wouldn't toggle otherwise. Confirm if can be changed -->
														<v-text-field
															:value="moment(enddate).format('MMMM Do, yyyy')"
															readonly
															dense
															outlined
															hide-details
															style="width:160px"
															class="my-0 ml-3 pa-0"
															@mousedown="repeattype = 'repeatuntil'"
															v-on="on"
														/>
													</template>
													<v-date-picker
														v-model="enddate"
														first-day-of-week="1"
														class="my-0"
														:min="moment().format('yyyy-MM-DD')"
														@input="enddatemethod"
													/>
												</v-menu>
											</span>
										</v-radio>
									</v-radio-group>
								</v-col>
							</v-row>
						</v-card-text>
					</v-card>
					<v-card-actions class="d-flex justify-end pa-1 pt-3">
						<v-btn color="blue" height="40" x-large text @click="dialog = false">Cancel</v-btn>
						<v-btn
							class="ml-2"
							height="40"
							x-large
							dark
							color="blue darken-3"
							@click="dialog = false"
						>Accept</v-btn>
					</v-card-actions>
				</v-card>
			</v-row>
		</v-card>
	</v-dialog>
</template>

<script>
import moment from "moment";
export default {
  props: {
    value: Boolean,
  },
	data() {
		return {
			moment: moment,
			// Schedule data //
			timemenu: false,
			startdatemenu: false,
			enddatemenu: false,
			time: "10:00",
			datearray: [moment().format("yyyy-MM-DD")],
			startdate: moment().format("yyyy-MM-DD"),
			enddate: moment().add(2, "w").format("yyyy-MM-DD"),
			days: [moment().day() ? moment().day() - 1 : 6],
			repeatfor: 1,
			repeattype: "repeatfor",
			// Red border to show invalid input, hint/message is hidden in text fields. Change if needed //
			valuerules: [(v) => v >= 0 || "Error", (v) => v <= 20 || "Error"],
		};
	},
	watch: {
		repeattype() {
			this.startdatemethod();
		},
		days() {
			this.startdatemethod();
		},
	},
  computed: {
    dialog: {
      get () {
        return this.value
      },
      set (value) {
         this.$emit('input', value)
      }
    }
  },
	methods: {
		startdatemethod() {
			if (this.repeattype === "repeatfor") {
				this.repeatformethod();
			} else if (this.repeattype === "repeatuntil") {
				this.enddatemethod();
			}
		},
		repeatformethod() {
			const first = this.startdate;
			// Breaks without days.length
			if (this.repeatfor > 0 && this.days.length) {
				// days array sorted to ensure all dates are in ascending order
				const days = this.days.slice().sort((a, b) => a - b);
				// addrepeat calculated to go to next week when a day greater than days is selected as startdate
				// Ex: greatest days is Friday, but Start Date is selected as Saturday
				// If day is greater, then for loop below is run one more time
				// -1 used because Sunday is 0, week starts from Sunday. Sets day as Monday.
				const addrepeat =
					days[days.length - 1] <
					(moment(first).day() ? moment(first).day() - 1 : 6)
						? 1
						: 0;
				// Set a date to Monday in the week, to calculate everything from there
				let start = moment(first).day(moment(first).day() ? 1 : -6);
				this.datearray = [];
				// Values concatenate for some reason, so +variable converts it to number
				for (let i = 0; i < +this.repeatfor + +addrepeat; i++) {
					// For every day in days, a new date is pushed corresponding to that day
					for (const day of days) {
						this.datearray.push(
							moment(start).add(day, "d").format("yyyy-MM-DD")
						);
					}
					// Goes to next week Monday and repeats
					start = moment(start).add(7, "d");
				}
				// Removes all dates before the first initial start date
				while (moment(first) > moment(this.datearray[0])) {
					this.datearray.shift();
				}
			} else {
				this.datearray = [first];
			}
		},
		enddatemethod() {
			const first = this.startdate;
			this.datearray = [first];
			// Only runs if enddate and some days present
			if (this.enddate && this.days.length) {
				let start = first;
				this.datearray = [];
				// Adds 1 day to start, every iteration, until it reaches enddate
				while (moment(this.enddate) >= moment(start)) {
					// Pushes value to datearray only if the day of start is present in selected days
					// -1 used because Sunday is 0, week starts from Sunday. Returns start day number subtracted by 1
					if (
						this.days.includes(
							moment(start).days() ? moment(start).days() - 1 : 6
						)
					) {
						this.datearray.push(start);
					}
					start = moment(start).add(1, "d").format("yyyy-MM-DD");
				}
			}
		},
	},
};
</script>

<style>
</style>