<template>
  <div class="home">

    <div class="m-5 notification-bar d-flex justify-content-center">
      <b-alert
        :show="dismissCountDown"
        fade
        animated
        :variant="variantAlert"
        @dismissed="dismissCountDown=0"
        @dismiss-count-down="countDownChanged"
      >
        <p>{{alertMessage}}</p>
        <b-progress
          :variant="variantAlert"
          :max="dismissSecs"
          :value="dismissCountDown"
          height="10px"
        ></b-progress>
      </b-alert>
    </div>

    <div class="container mt-5">
      <div class="row">
        <div class="col-md-6 justify-content-between d-flex dashboard-tab">
          <div class="d-flex flex-column justify-content-center timer-display">
            <p>{{todayDate}}</p>
            <p id="timer">{{timer}}</p>
          </div>
          <div class="d-flex flex-column justify-content-between">
            <button type="button" @click="startTimer" class="m-1 btn btn-primary">Empezar</button>
            <button type="button" @click="stopTimer" class="m-1 btn btn-danger">Parar</button>
            <button type="button" @click="pauseTimer" class="m-1 btn btn-success">Descanso</button>
          </div>
        </div>
        <div class="col-md-6 justify-content-between d-flex dashboard-tab"></div>
      </div>

      <div class="row">
        <div class="col-md-6 justify-content-between d-flex dashboard-tab"></div>
        <div class="col-md-6 justify-content-between d-flex dashboard-tab"></div>
      </div>

      <div class="row">
        <div class="col-md-6 justify-content-between d-flex dashboard-tab"></div>
        <div class="col-md-6 justify-content-between d-flex dashboard-tab"></div>
      </div>
    </div>
  </div>
</template>

<script>
import Timer from "easytimer";
import dateFormat from "dateformat";
//Create an instance of the timer used to track the time spent working
let easytimer = new Timer();
//Attach events to correspondent div
easytimer.addEventListener("secondsUpdated", function(e) {
  document.getElementById(
    "timer"
  ).innerHTML = easytimer.getTimeValues().toString();
});
easytimer.addEventListener("secondsUpdated", function(e) {
  document.getElementById(
    "timer"
  ).innerHTML = easytimer.getTimeValues().toString();
});
easytimer.addEventListener("started", function(e) {
  document.getElementById(
    "timer"
  ).innerHTML = easytimer.getTimeValues().toString();
});
easytimer.addEventListener("reset", function(e) {
  document.getElementById(
    "timer"
  ).innerHTML = easytimer.getTimeValues().toString();
});

export default {
  name: "home",
  data() {
    return {
      todayDate: "",
      timer: "",
      dismissSecs: 10,
      dismissCountDown: 0,
      showDismissibleAlert: false,
      alertMessage: "",
      variantAlert: "danger"
    };
  },
  components: {},
  methods: {
    startTimer() {
      console.log("Timer started");
      easytimer.start();
      this.variantAlert = "primary";
      this.alertMessage = "Has comenzado la jornada laboral";
      this.dismissCountDown = this.dismissSecs;
    },
    stopTimer() {
      console.log("Timer stopped");
      easytimer.stop();
      this.variantAlert = "danger";
      this.alertMessage = "Has finalizado la jornada laboral";
      this.dismissCountDown = this.dismissSecs;
      this.timer = easytimer.getTimeValues().toString();
    },
    pauseTimer() {
      console.log("Timer paused");
      this.variantAlert = "success";
      this.alertMessage = "Has comenzado tu descanso";
      this.dismissCountDown = this.dismissSecs;
      easytimer.pause();
    },
    countDownChanged(dismissCountDown) {
      this.dismissCountDown = dismissCountDown;
    }
  },
  created() {
    this.timer = easytimer.getTimeValues().toString();
    this.todayDate = dateFormat(new Date(), "dddd, mmmm dS, yyyy");
  }
};
</script>

<style  scoped>

.dashboard-tab {
  border: 1px solid black;
  height: 10rem;
}
.timer-display {
  width: 100%;
  font-size: 20px;
}
#timer {
  font-size: 55px;
}

.notification-bar {
  height: 8rem;
}
</style>
