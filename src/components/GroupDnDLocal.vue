<template>
  <div>
    <div class="groups">
      <!-- NOTE: Find a way to condense code below -->
      <!-- Course Basket -->
      <div class="group">
        <div class="container-crown">
          <h2>Course Basket</h2>

          <!-- Roster Selector -->
          <label>Roster:</label>
          <select v-model="selectedRoster" v-on:change="loadCourses">
            <option v-for="roster in rosterList">{{ roster }}</option>
          </select>

          <!-- Search Bar -->
          <v-select
            v-model="selectedCourse"
            placeholder="Add a course"
            @input="addToBasket(selectedCourse)"
            :options="courseList"
            class="style-chooser"
          ></v-select>
        </div>

        <!-- Basket container -->
        <Container
          group-name="1"
          :get-child-payload="getChildPayload0"
          @drop="onDrop('basket', $event)"
          :drop-placeholder="dropPlaceholder"
          :remove-on-drop-out="true"
          class="container"
        >
          <Draggable v-for="item in basket" :key="item.id">
            <div class="draggable-item">
              {{ item.code }}
              <br />
              <p class="subtext">
                {{ item.credits }} Credits
                <br />
                {{ item.offered }}
                <br />
              </p>
            </div>
          </Draggable>
        </Container>
      </div>

      <!-- Schema Table (years 1, 2, 3, 4) -->
      <div class="group">
        <!-- Freshman Fall -->
        <div>
          <div class="container-crown">
            <h2>Freshman Fall</h2>
            <p>{{ items1.length }} Courses</p>
            <p>{{ totalCredits }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload1"
            @drop="onDrop('items1', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items1" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>

        <!-- Freshmen Spring -->
        <div>
          <div class="container-crown">
            <h2>Freshman Spring</h2>
            <p>{{ items2.length }} Courses</p>
            <p>{{ totalCredits2 }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload2"
            @drop="onDrop('items2', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items2" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>
      </div>

      <!-- Soph -->
      <div class="group">
        <!-- Soph Fall -->
        <div>
          <div class="container-crown">
            <h2>Sophomore Fall</h2>
            <p>{{ items3.length }} Courses</p>
            <p>{{ totalCredits3 }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload3"
            @drop="onDrop('items3', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items3" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>

        <!-- Soph Spring -->
        <div>
          <div class="container-crown">
            <h2>Sophomore Spring</h2>
            <p>{{ items4.length }} Courses</p>
            <p>{{ totalCredits4 }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload4"
            @drop="onDrop('items4', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items4" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>
      </div>

      <!-- Junior -->
      <div class="group">
        <!-- Junior Fall -->
        <div>
          <div class="container-crown">
            <h2>Junior Fall</h2>
            <p>{{ items5.length }} Courses</p>
            <p>{{ totalCredits5 }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload5"
            @drop="onDrop('items5', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items5" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>

        <!-- Junior Spring -->
        <div>
          <div class="container-crown">
            <h2>Junior Spring</h2>
            <p>{{ items6.length }} Courses</p>
            <p>{{ totalCredits6 }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload6"
            @drop="onDrop('items6', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items6" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>
      </div>

      <!-- Senior -->
      <div class="group">
        <!-- Senior Fall -->
        <div>
          <div class="container-crown">
            <h2>Senior Fall</h2>
            <p>{{ items7.length }} Courses</p>
            <p>{{ totalCredits7 }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload7"
            @drop="onDrop('items7', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items7" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>

        <!-- Senior Spring -->
        <div>
          <div class="container-crown">
            <h2>Senior Spring</h2>
            <p>{{ items8.length }} Courses</p>
            <p>{{ totalCredits8 }} Credits</p>
          </div>
          <Container
            group-name="1"
            :get-child-payload="getChildPayload8"
            @drop="onDrop('items8', $event)"
            :drop-placeholder="dropPlaceholder"
            :remove-on-drop-out="true"
            class="container"
          >
            <Draggable v-for="item in items8" :key="item.id">
              <div class="draggable-item">
                {{ item.code }}
                <br />
                <p class="subtext">
                  {{ item.credits }} Credits
                  <br />
                  {{ item.offered }}
                  <br />
                </p>
              </div>
            </Draggable>
          </Container>
        </div>
      </div>

      <!-- end -->
    </div>
  </div>
</template>

<script>
import vSelect from "vue-select";
import { Container, Draggable } from "vue-smooth-dnd";
import { applyDrag, generateItems } from "../utils/helpers";

import SP19 from "../assets/localdata/sp19.json";
import FA19 from "../assets/localdata/fa19.json";

export default {
  name: "Groups",
  components: { Container, Draggable, vSelect },
  data() {
    return {
      // SEARCH BAR
      courseList: [],
      search: "",
      selectedCourse: "",
      selectedRoster: " ",
      rosterList: ["FA19", "SP19"],
      basket: [],

      // LOCAL DATA
      localJson: {
        rosters: {
          FA19,
          SP19
        }
      },

      // DRAG AND DROP
      // scene,
      dropPlaceholder: {
        className: "ghost",
        animationDuration: "150",
        showOnTop: true
      },
      items1: [],
      items2: [],
      items3: [],
      items4: [],
      items5: [],
      items6: [],
      items7: [],
      items8: []
    };
  },
  created() {
    // Load rosters
    // no need
  },

  computed: {
    totalCredits: function() {
      return this.items1.reduce((acc, item) => acc + item.credits, 0);
    },
    totalCredits2: function() {
      return this.items2.reduce((acc, item) => acc + item.credits, 0);
    },
    totalCredits3: function() {
      return this.items3.reduce((acc, item) => acc + item.credits, 0);
    },
    totalCredits4: function() {
      return this.items4.reduce((acc, item) => acc + item.credits, 0);
    },
    totalCredits5: function() {
      return this.items5.reduce((acc, item) => acc + item.credits, 0);
    },
    totalCredits6: function() {
      return this.items6.reduce((acc, item) => acc + item.credits, 0);
    },
    totalCredits7: function() {
      return this.items7.reduce((acc, item) => acc + item.credits, 0);
    },
    totalCredits8: function() {
      return this.items8.reduce((acc, item) => acc + item.credits, 0);
    }
  },

  methods: {
    // Load courses when roster changes
    loadCourses: function() {
      // Clean course list
      this.courseList = [];

      // Add courses to course list
      var JSONcourses = this.localJson.rosters[this.selectedRoster][
        this.selectedRoster
      ];

      for (var course in JSONcourses) {
        this.courseList.push(JSONcourses[course]);
      }
    },

    // SEARCH BAR
    addToBasket: function(selectedCourse) {
      // Prevent pushing a duplicate course
      if (!this.basket.includes(selectedCourse)) {
        this.basket.push(selectedCourse);
      }
    },

    //DRAG AND DROP
    onDrop(collection, dropResult) {
      this[collection] = applyDrag(this[collection], dropResult);
    },

    getChildPayload0(index) {
      return this.basket[index];
    },
    getChildPayload1(index) {
      return this.items1[index];
    },
    getChildPayload2(index) {
      return this.items2[index];
    },
    getChildPayload3(index) {
      return this.items3[index];
    },
    getChildPayload4(index) {
      return this.items4[index];
    },
    getChildPayload5(index) {
      return this.items5[index];
    },
    getChildPayload6(index) {
      return this.items6[index];
    },
    getChildPayload7(index) {
      return this.items7[index];
    },
    getChildPayload8(index) {
      return this.items8[index];
    }
    // SearchBar
    // addToBasket: function(selectedCourse){
    //     this.basket.push(selectedCourse);
    // }
  }
};
</script>

<style lang="scss">
// no scope else draggable container and v-select styling will not work

// Variables
$box-bg-color: #1f262a;
$container-bg-color: rgb(78, 78, 82);
$draggable-bg: #ffbf00;

$draggable-text-color: #361b28;
//  #1F262A;

$ghost-bg-color: #ffc60b;
$ghost-border: 2px dashed #ff8b00;

$h2-text-color: #c0c0c0;
$p-text-color: #c0c0c0;
$p-font: Verdana, Arial, sans-serif;

$select-bg: #c0c0c0;

p {
  color: $p-text-color;
  font-style: $p-font;
}

.groups {
  display: flex;
  /* justify-content: stretch; */
  margin-top: 50px;
  margin-right: 50px;
}
.group {
  /* flex: 1; */
  margin: 8px;
  padding: 12px;
  width: 200px;
  min-height: 300px;
  background-color: $box-bg-color;
  border-radius: 8px;
  // box-shadow: 0px 0px 16px darkslategray;
}

// .container-crown {
//   height: 120px;
// }

.container {
  background-color: $container-bg-color;
  padding: 6px 0;
  min-height: 120px;
}

.draggable-item {
  padding: 4px;
  margin: 6px 12px;
  background-color: $draggable-bg;
  color: $draggable-text-color;
  text-align: center;
}

h2 {
  margin: 0;
  padding: 0;
  font-size: 22px;
  color: $h2-text-color;
}

.ghost {
  opacity: 0.65;
  border: $ghost-border;
  background-color: $ghost-bg-color;
}

.draggable-item,
.ghost,
container {
  border-radius: 6px;
}

.subtext {
  font-size: 16px;
  text-align: right;
  color: $draggable-text-color;
  margin: 0;
}

//LOADING
.hidden {
  display: none;
}

/* Vue-select */
@import "vue-select/src/scss/vue-select.scss";

.v-select {
  border-radius: 6px;
  background-color: $select-bg;
}

// .v-select :hover {
//   background-color: white;
//   transition-duration: 100ms;
// }

// Prevents users from using the 'x' function of the search bar.
// the 'x' function is buggy
.style-chooser .vs__clear {
  visibility: hidden;
}

.style-chooser .vs__dropdown-menu {
  max-height: 240px;
}
</style>