<template>
  <div class="content">
    <p class="date">
      {{ my_time.year }}-{{ my_time.month }}-{{ my_time.day }} 星期{{
        my_time.weekDay
      }}
    </p>
    <p class="time">
      {{ my_time.hour }}:{{ my_time.minute }}:{{ my_time.second }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      timer: null,
      my_time: {
        year: "",
        month: "",
        day: "",
        weekDay: "",
        hour: "",
        minute: "",
        second: "",
      },
    };
  },
  mounted() {
    clearInterval(this.timer);
    this.timer = null;
    this.setTimer();
  },
  destroyed() {
    clearInterval(this.timer);
    this.timer = null;
  },
  methods: {
    getLocalTime() {
      let my_date = new Date();
      this.my_time.year = my_date.getFullYear();
      this.my_time.month =
        my_date.getMonth() + 1 > 10
          ? my_date.getMonth() + 1
          : "0" + (my_date.getMonth() + 1);
      this.my_time.day =
        my_date.getDate() > 10 ? my_date.getDate() : "0" + my_date.getDate();
      this.my_time.weekDay = this.changeWeekDay(my_date.getDay());
      this.my_time.hour =
        my_date.getHours() > 10 ? my_date.getHours() : "0" + my_date.getHours();
      this.my_time.minute =
        my_date.getMinutes() > 10
          ? my_date.getMinutes()
          : "0" + my_date.getMinutes();
      this.my_time.second =
        my_date.getSeconds() > 10
          ? my_date.getSeconds()
          : "0" + my_date.getSeconds();
    },
    changeWeekDay(weekDay) {
      let str = "";
      if (weekDay == 0) {
        str = "日";
      } else if (weekDay == 1) {
        str = "一";
      } else if (weekDay == 2) {
        str = "二";
      } else if (weekDay == 3) {
        str = "三";
      } else if (weekDay == 4) {
        str = "四";
      } else if (weekDay == 5) {
        str = "五";
      } else {
        str = "六";
      }
      return str;
    },
    setTimer() {
      if (this.timer == null) {
        this.timer = setInterval(() => {
          this.getLocalTime();
        }, 1000);
      }
    },
  },
};
</script>

<style>
.content {
  font-family: "Share Tech Mono", monospace;
  color: #fff;
  text-align: center;
  position: absolute;
  left: 50%;
  top: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  color: #daf6ff;
  text-shadow: 0 0 20px #0aafe6, 0 0 20px rgb(10 175 230 / 0%);
}
.date {
  letter-spacing: 0.1em;
  font-size: 24px;
}
.time {
  letter-spacing: 0.05em;
  font-size: 80px;
  padding: 20px 0 0;
}
p {
  margin: 0;
  padding: 0;
  display: block;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
}
</style>