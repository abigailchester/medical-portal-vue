  <!-- <div>
    <h1>testing element</h1>
    <el-button>button</el-button>
  </div> -->
  <template>
  <main>
    <el-container>
    <div class="el-card is-always-shadow" id="window">
      <el-row id="title">
        <span>Immunization Details<i style="float:right" class="el-icon-close"></i></span>
      </el-row>
      <el-row id="patientDetails">
        <span>
          <img src="../assets/icon.png" style="height: 25px; transform: translateY(5px)">
          <span>{{ name }}</span>
          <!-- <el-divider direction="vertical"></el-divider>{{ calculateAge() }} Months, {{ sex }} <el-divider direction="vertical"></el-divider> DOB {{ birthDate }}<i style="float:right" class="el-icon-arrow-down"></i> -->
          <el-divider direction="vertical"></el-divider>18 Months, {{ sex }} <el-divider direction="vertical"></el-divider> DOB {{ birthDate }}<i style="float:right" class="el-icon-arrow-down"></i>
        </span>
      </el-row>
      <el-row>
        <div id="formWindow">
        <el-col id="menuBar">
          <el-row style="margin:12px">
            <el-input 
              style="width:85%" 
              placeholder="Search" 
              size="mini" 
              prefix-icon="el-icon-search" 
              suffix-icon="el-icon-star-off"
            >
              <i slot="suffix"><el-divider direction="vertical"></el-divider></i>
            </el-input>
            <el-button size="mini" icon="el-icon-plus"></el-button>
          </el-row>
            <div 
              v-for="(vaccine, index) in vaccines" 
              :key="vaccine.vaccineId" 
              :class="{ selected: selectedVaccine == index }" 
              style="padding:12px" @click="updateVaccine(index)"
            >
              <el-row>
                <span><b>{{vaccine.name}}</b></span>
                <span 
                  class="status" 
                  :class="{ inactive: !vaccine.active }" 
                  style="float: right; font-size: x-small"
                >
                  {{vaccine.status}}
                </span>
              </el-row>
              <el-row>
                <span style="color: grey; font-size: x-small">
                  {{vaccine.due}}
                </span>
              </el-row>
            </div>
          <el-row style="position:absolute;bottom:10px; left:10px">
            <a href="">View Immunization Schedule</a>
          </el-row>
        </el-col>
        <el-col>
          <el-row style="background-color:#F8F9FE;">
            <div id="innerForm">
            <el-col style="padding:23px; padding-right: 8px; padding-bottom:33px">
              <el-row>
                <span>Details</span>
                <span style="float: right">
                  <a href="">Add Standing Instructions</a>
                  <i style="color: grey" class="el-icon-info"></i>
                </span>
              </el-row>
              <el-row :gutter="12">
                <el-col :span=8>
                  <label>Visit Date<el-input size="mini" v-model="details.visitDate" suffix-icon="el-icon-date"></el-input></label>
                </el-col>
                <el-col :span=8>
                  <label>Exp. Date<el-input size="mini" v-model="details.expDate" suffix-icon="el-icon-date"></el-input></label>
                </el-col>
                <el-col :span=8>
                  <label>Status<el-input size="mini" v-model="details.status" suffix-icon="el-icon-caret-bottom"></el-input></label>
                </el-col>
              </el-row>
              <el-row :gutter="13">
                <el-col :span=16>
                  <label>Reason<el-input size="mini" suffix-icon="el-icon-more"><i slot="suffix"><el-divider direction="vertical"></el-divider></i></el-input></label>
                  <!-- <label>Reason<div class="el-input el-input--mini el-input--suffix"><input type="text" class="el-input__inner"><span class="el-input__suffix"><span class="el-input__suffix-inner"><el-divider direction="vertical"></el-divider><i class="el-input__icon el-icon-more"></i></span></span></div></label> -->
                  <!-- <label>Reason<div :class="inputClass"><input type="text" class="el-input__inner"><span class="el-input__suffix"><span class="el-input__suffix-inner"><el-divider direction="vertical"></el-divider><i class="el-input__icon el-icon-more"></i></span></span></div></label> -->
                </el-col>
              </el-row>
              <el-divider></el-divider>
              <el-row :gutter=11>
                <el-col :span=8>
                  <label>Dose Number<el-input size="mini" v-model="details.doseNumber"></el-input></label>
                </el-col>
                <el-col :span=8>
                    <el-row>
                    <!-- <el-col :span=11><label>Dose<el-input size="mini"></el-input></label></el-col> -->
                    <!-- <el-col :span=11><el-input size="mini"></el-input></el-col> -->
                    <label>Dose
                        <div>
                        <el-input size="mini" v-model="details.dose" style="width:48%">
                        <i slot="suffix" class="el-icon-minus"></i>
                        <i style="margin-right:-4px; margin-left:-3px" slot="suffix">
                          <el-divider direction="vertical"></el-divider>
                        </i>
                        <i slot="suffix" class="el-input__icon el-icon-plus">
                        </i>
                        </el-input>
                        <el-input size="mini" style="width:48%;margin-left:5px;" v-model="details.doseAmount">
                            <i slot="suffix" class="el-icon-caret-bottom" style="line-height:2.4;"></i>
                        </el-input></div></label>
                    </el-row>
                </el-col>
                <!-- <el-col :span=8>
                    <label>
                      <div>Dose</div> -->
                      <!-- Dose -->
                      <!-- <el-input size="mini" style="width:46%" v-model="details.dose">
                        <i slot="suffix" class="el-icon-minus"></i>
                        <i style="margin-right:-4px; margin-left:-3px" slot="suffix">
                          <el-divider direction="vertical"></el-divider>
                        </i>
                        <i slot="suffix" class="el-input__icon el-icon-plus">
                        </i>
                      </el-input> -->
                    <!-- </label>
                    <el-input 
                      class="caretBottom" 
                      size="mini" 
                      suffix-icon="el-icon-caret-bottom" 
                      style="width:48%; float:right" 
                      v-model="details.doseAmount"
                    > -->
                    <!-- <el-input 
                      class="caretBottom" 
                      size="mini" 
                      style="width:48%; float:right;" 
                      v-model="details.doseAmount"
                    > -->
                        <!-- <i slot="suffix" class="el-icon-caret-bottom" style="margin:auto 0"></i> -->
                        <!-- <i slot="suffix" class="el-icon-caret-bottom" style="margin:auto 0"></i> -->
                        <!-- <i slot="suffix" class="el-icon-caret-bottom" style="line-height:2.1"></i> -->
                        <!-- <i slot="suffix" class="el-icon-caret-bottom" style="line-height:2.1;"></i> -->
                        <!-- <i class="el-icon-caret-bottom" style="line-height:2.1;"></i> -->
                    <!-- </el-input> -->
                <!-- </el-col> -->
                <el-col :span=8>
                  <label>
                    Lot Number
                    <el-input 
                      size="mini" 
                      suffix-icon="el-icon-more" 
                      v-model="details.lotNumber"
                    >
                      <i slot="suffix">
                        <el-divider direction="vertical"></el-divider> 
                      </i>
                    </el-input>
                  </label>
                </el-col>
              </el-row>
              <el-row>
                <label for="route">
                  <div>Route</div>
                </label>
                <el-radio-group v-model="details.route">
                  <el-radio label="Injectible"></el-radio>
                  <el-radio label="Oral"></el-radio>
                  <el-radio label="Intraveneous"></el-radio>
                </el-radio-group>
              </el-row>
              <el-divider></el-divider>
              <el-row :gutter="11">
                <el-col :span="8">
                  <label>Given Date
                    <el-input 
                      size="mini" 
                      :v-model="details.givenDate" 
                      :placeholder="details.visitDate" 
                      suffix-icon="el-icon-date"
                    >
                    </el-input>
                  </label>
                </el-col>
                <el-col :span="16">
                  <!-- <label>Given By -->
                    <!-- <el-input 
                      size="mini" 
                      prefix-icon="el-icon-search" 
                      suffix-icon="el-icon-more"
                    >
                      <i slot="suffix" class="el-icon-caret-bottom">
                        <el-divider direction="vertical"></el-divider>
                      </i>
                      <i slot="suffix" class="el-icon-star-off">
                        <el-divider direction="vertical"></el-divider>
                      </i>
                    </el-input>
                  </label>
                </el-col>
                <el-col :span="16" offset="8">
                  <div class="el-input el-input--mini el-input--prefix el-input--suffix">
                    <input type="text" class="el-input__inner">
                    <span class="el-input__prefix">
                      <i class="el-input__icon el-icon-search"></i>
                    </span>
                    <span class="el-input__suffix">
                      <span class="el-input__suffix-inner">
                        <i class="el-input__icon el-icon-caret-bottom"></i>
                        <el-divider direction="vertical"></el-divider>
                        <i class="el-input__icon el-icon-star-off"></i>
                        <el-divider direction="vertical"></el-divider>
                        <i class="el-input__icon el-icon-more"></i>
                      </span>
                    </span>
                  </div>
                </el-col>
                <el-col :span="16" offset="8">
                  <div class="el-input el-input--mini el-input--prefix el-input--suffix">
                    <input type="text" class="el-input__inner">
                    <span class="el-input__prefix">
                      <i class="el-input__icon el-icon-search"></i>
                    </span>
                    <span class="el-input__suffix">
                      <span class="el-input__suffix-inner">
                        <i class="el-icon-caret-bottom"></i>
                        <el-divider direction="vertical"></el-divider>
                        <i class="el-icon-star-off"></i>
                        <el-divider direction="vertical"></el-divider>
                        <i class="el-input__icon el-icon-more"></i>
                      </span>
                    </span>
                  </div>
                </el-col> -->
                <!-- <el-col :span="16" offset="8"> -->
                  <label>Given By
                    <div class="el-input el-input--mini el-input--prefix el-input--suffix">
                      <input type="text" class="el-input__inner">
                      <span class="el-input__prefix">
                        <i class="el-input__icon el-icon-search"></i>
                      </span>
                      <span class="el-input__suffix">
                        <span class="el-input__suffix-inner">
                          <i class="el-icon-caret-bottom"></i>
                          <el-divider direction="vertical"></el-divider>
                          <i class="el-icon-star-off"></i>
                          <el-divider direction="vertical"></el-divider>
                          <i class="el-input__icon el-icon-more"></i>
                        </span>
                      </span>
                    </div>
                  </label>
                </el-col>
              </el-row>
              <el-row :gutter="11">
                <el-col :span="8">
                  <label>Given Time
                    <el-input 
                      size="mini" 
                      v-model="details.givenTime" 
                      suffix-icon="el-icon-time"
                    >
                    </el-input>
                  </label>
                </el-col>
                <el-col :span="8">
                  <label>Manufacturer
                    <el-input 
                      size="mini" 
                      placeholder="Select" 
                      v-model="details.manufacturer" 
                      suffix-icon="el-icon-caret-bottom">
                    </el-input>
                  </label>
                </el-col>
                <el-col :span="8">
                  <label>Location
                    <el-input 
                      size="mini" 
                      placeholder="Select" 
                      v-model="details.location" 
                      suffix-icon="el-icon-caret-bottom">
                    </el-input>
                  </label>
                </el-col>
              </el-row>
            </el-col>
            <el-col style="padding:13px">
            <!-- <el-col style="padding:25px"> -->
              <div id="whitecol">
              <el-row>Assessments</el-row>
              <el-row>
                <el-checkbox>Select All</el-checkbox>
              </el-row>
              <el-row>
                <!-- <el-divider></el-divider> -->
                <div 
                  v-for="assessment in assessmentOptions" 
                  :key="assessment"
                >
                  <el-checkbox 
                    v-model="completedAssessments" 
                    :label="assessment"
                  >
                  </el-checkbox>
                  <!-- <el-divider></el-divider> -->
                </div>
              </el-row>
              <el-row>
                <h4><i class="el-input__icon el-icon-arrow-right"></i>Comments</h4>
                <!-- <h4><i class="el-icon-arrow-right"></i>Comments</h4> -->
              </el-row>
              <el-row id="bottomCheckboxes">
                <div>
                  <el-checkbox 
                    v-model="decrementDose" 
                    label="Decrement the Dose"
                  >
                  </el-checkbox>
                  <el-checkbox 
                    v-model="isBillable" 
                    label="Billable"
                  >
                  </el-checkbox>
                </div>
              </el-row>
              </div>
            </el-col>
            </div>
          </el-row>
        </el-col>
        </div>
      </el-row>
      <el-row style="border-top: 1px solid lightgrey;">
        <el-col style="padding:13px 10px" align="right">
          <el-button size="mini">
            <span>Cancel</span>
          </el-button>
          <el-button 
            size="mini" 
            style="color: white; background-color: #326DE6"
          >
            <span>Save</span>
          </el-button>
        </el-col>
      </el-row>
    </div>
    </el-container>

  </main>
</template>

<script>
export default {
  name: 'MedPortal',
  props: {
    msg: String
  },
  data() {
    return {
      name: 'Willis, Ben',
      type: 'date',
      sex: 'Male',
      birthDate: '09/15/2018',
      selectedVaccine: 0,
      vaccines: [
        {
          vaccineId: 2234,
          name: 'Hepatitis B',
          active: true,
          due: "Due: 3rd Dose (6 - 15 mos)",
          status: 'active',
          details: {
            visitDate: '01/22/2020',
            expDate: '09/20/2021',
            status: 'Pending',
            reason: null,
            doseNumber: 2563232564545,
            dose: 3,
            doseAmount: '10 mcg',
            lotNumber: 'INE032625',
            route: 'Injectible',
            givenDate: '01/22/2020',
            gave: {
              type: Date, 
              value: '01/01/2020'
              },
            givenBy: null,
            givenTime: '10:45 AM',
            manufacturer: null,
            location: null,
          },
        },
        {
          vaccineId: 2235,
          name: 'Influenza',
          active: true,
          due: "Due: Annual Vaccination (6 - 15 mos)",
          status: 'active'
        },
        {
          vaccineId: 2236,
          name: 'Pneumococcal',
          active: false,
          status: 'inactive'
        },
        {
          vaccineId: 2237,
          name: 'Rotavirus',
          active: false,
          status: 'inactive'
        },
      ],
      assessmentOptions: ["A48.51 Infant botulism", "G93.7 Reye's syndrome", "R68.11 Excessive crying of infant"],
      completedAssessments: ["A48.51 Infant botulism"],
      selectedAssessments: ["d"],
      selectAll: false,
      comments: ['complete assessments'],
      decrementDose: true,
      isBillable: true,
      inputClass: 'el-input el-input--mini el-input--suffix',
    }
  },
  methods: {
    startHacking () {
      this.$notify({
        title: 'It works!',
        type: 'success',
        message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
        duration: 5000
      })
    },
    updateVaccine(index) {
      this.selectedVaccine = index
    },
    // calculateAge() {
    //   var d = new Date()
    // //   var bday = new Date(1994, 1, 3)
    // //   var his = Date()
    //   var y = d.getFullYear()
    //   var m = d.getMonth()
    //   var day = d.getDate()
    //   var now = Date.now()
    //   var bennay = new Date(this.birthDate)
    //   var parsedBirthDate = Date.parse(this.birthDate)
    //   var time = now - parsedBirthDate
    // //   var longer = 1000*60*60*24*30*365
    //   var calculateMonths = 1000*60*60*24*30
    //   var birthyear = bennay.getFullYear() //2018
    //   var birthmonth = bennay.getMonth()   //8
    //   var hisbirthday = bennay.getDate()   //15
    //   var ageInYears = y - birthyear
    //   var age_month = m - birthmonth
    //   var age_day = day - hisbirthday      

    //   if(age_month < 0 || (age_month == 0 && age_day < 0)) {
    //     ageInYears = parseInt(ageInYears) -1;
    //   }

    //   var ageBeforeRounding = time / calculateMonths
    //   var age = Math.floor(ageBeforeRounding)
    //   return age
    // },
    pickDate() {
      alert()
    },
    select() {
      this.selectedAssessments = [];
      if (!this.selectAll) {
        for (let i in this.assessmentOptions) {
          this.selectedAssessments.push(this.assessmentOptions[i]);
        }
      }
    },
    selecting(index) {
      this.selectedVaccine = index
    },
    closing() {
      var y = document.getElementById("window")
      alert("do you want to save?")
      y.remove()
    },
    switchDate() {
      var dating = document.getElementsByClassName('el-input__prefix')
      console.log(dating[0])
      var i;
      for (i = 0; i < dating.length; i++) {
        dating[i].removeAttribute('class')
        dating[i].setAttribute('class', 'el-input__suffix')
      }
    },
    bird() {
      var bird = document.getElementById('realbirdy')
      bird.removeAttribute('class')
      bird.setAttribute('class', 'el-input__suffix')
    }
  },
  computed: {
    details() {
      return this.vaccines[this.selectedVaccine].details
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */

/* #app { */

/* main {
  font-family: Helvetica, sans-serif;
  font-size: small;
  background-color: #BECEF5;
  min-height: 100vh;
  line-height: 1.7;
} */

#window {
  margin: 30px; 
  width: 100%; 
  border-radius:10px; 
  background-color:white;
}

#title {
  background-color: rgb(69,79,98); 
  color:white; 
  padding:12px;
}

#patientDetails {
  box-shadow: 0 5px 10px #EAEBED; 
  z-index: 10; 
  padding:12px;
}

#menuBar {
  height:100%; 
  box-shadow: 5px 0 10px #EAEBED; 
  z-index: 5
}

#whitecol {
  background-color:white; 
  height:100%;
  padding-right:11px;
  padding-left:15px;
  /* position */
  /* text-align: left; */
  /* align-items: left; */
  /* align-content: left; */
  /* display: block; */
  /* align-items: left; */
}

#whitecol > .el-row {
    /* margin: 10px; */
}

label {
  color: grey;
  font-size: x-small;
}
.el-card {
  border: 1px solid lightgrey;
}

#bottomCheckboxes {
  position: absolute;
  bottom: 30px;
}

#formWindow {
  display: grid;
  grid-template-columns: 24% 76%;
}
#innerForm {
  display: grid;
  grid-template-columns: 2fr 1.16fr;
}

i:hover {
  /* border-style: solid;
  border-color: aquamarine;
  background-color: pink; */
  cursor: pointer;
}

.selected {
  background-color: #EAF0FC;
  border-top: 1px solid rgba(101,126,167,0.49);
  border-bottom: 1px solid rgba(101,126,167,0.49);
  box-shadow: #356CD8 0 1px 3px;
}
a {
  color: rgba(96,119,144,0.83);
}

.status {
  border: 1px grey;
  border-style: solid;
  border-radius: 12px;
  background-color: #ffffff;
  color: green;
  text-transform: uppercase;
  padding-left: 3px;
  padding-right: 3px;
}
.inactive {
  color:grey;
  background-color: lightgrey;
}

.active {
  border: 1px #97999C;
  border-style: solid;
  background-color: white;
  color: green;
  width: max-content;
  border-radius: 12px;
  padding: 2px;
  margin: 2px;
  float: right;
}
.not {
  color: grey;
  background-color: lightgray;
}

.el-checkbox__inner {
  border: 1px solid lightgrey;
}
.el-checkbox__inner::after {
  border-style: solid;
  border-color: rgb(78, 99, 133);
}
span.el-radio__input.is-checked > span.el-radio__label {
  background-color: white;
}

.el-radio__label {
  color:#545454;
  font-size: x-small;
  padding-left: 5px;
}
.el-radio {
  margin-right: 20px;
}

.el-radio__input.is-checked > .el-radio__inner {
  background-color: white;
}

.el-radio__inner::after {
  background-color: #356CD8;
  border: 1px solid #356CD8;
}

span.el-checkbox__input.is-checked > span.el-checkbox__inner {
  background-color: white;
}
.el-radio.is-checked > .el-radio__label {
  color:#4C4D51;
}
.el-checkbox.is-checked > .el-checkbox__label, .el-checkbox  {
  color: #0A0A0A;
}

.el-input__inner {
  padding: 0 7px;
}
.el-input__suffix {
  color: grey;
}
.el-input__prefix {
  color: #C0C4CC;
}

span.el-input__suffix-inner > i.el-input__icon {
margin-left:-6px;
margin-right:-1px;
}
.el-icon-star-off {
  /* color:green; */
  margin-left: -1px;
  margin-right: -1px;
}

.el-icon-minus {
  /* color:blue; */
  font-size: 9px;
  color:rgb(66, 66, 66);
  /* color: black; */
  padding-right:3px;

}
span.el-input__suffix-inner > i.el-input__icon.el-icon-plus {
  /* color: black; */
  color: rgb(66, 66, 66);
  font-size: 9px;
  margin-right: -7px;
}
.el-button--mini {
  border-radius: 5px;
  font-size: x-small;
  padding: 7px 11px;
}
.el-input+.el-button {
  margin-left:7px;
  background-color: #EFF0F2;
  padding:8px 6px;
}
.el-button+.el-button {
  margin-left: 7px;
}

/* div.el-input.caretBottom > .el-input__inner {
  padding-right: 20px;
} */
.el-input__suffix .el-input__inner {
    padding: 0;
}

div.el-input.caretBottom > span.el-input__suffix > span.el-input__suffix-inner > i.el-input__icon.el-icon-caret-bottom {
  color: black;
  margin-right: -6px;
}

</style>
