<template>
  <div>
    <div class="block">
      <el-timeline>
        <el-timeline-item
          v-for="(activity, index) in activities"
          :key="index"
          :icon="activity.icon"
          :type="activity.type"
          :color="activity.color"
          :size="activity.size"
          :timestamp="activity.timestamp">
          {{activity.content}}
        </el-timeline-item>
      </el-timeline>
    </div>
  </div>
</template>

<script>
export default {
  name: "CreateProcess",
  data() {
    return {
      activities:[]
    }
  },
  mounted() {
    const ws = new WebSocket("ws://localhost:8089/websocket");
    ws.onopen = () => {
      console.log("connected");
    };
    ws.onmessage = event => {
      const obj = JSON.parse(event.data);
      const step = obj.step;
      if (step === 1){
        this.activities.push({
          content: obj.user + " create request " + obj.task + " task",
          timestamp: obj.time,
          size: 'large',
          type: 'primary',
          icon: 'el-icon-more'
        });
      } else if (step === 2){
        this.activities.push({
          icon: "el-icon-edit",
          type: "primary",
          color: "green",
          size: "large",
          timestamp: "2019-01-01 12:00:00",
          content: "Edit file"
        });
      } else if (step === 3){
        this.activities.push({
          icon: "el-icon-view",
          type: "primary",
          color: "green",
          size: "large",
          timestamp: "2019-01-01 12:00:00",
          content: "View file"
        });
      } else if (step === 4){
        this.activities.push({
          icon: "el-icon-download",
          type: "primary",
          color: "green",
          size: "large",
          timestamp: "2019-01-01 12:00:00",
          content: "Download file"
        });
      }
    };
    ws.onclose = () => {
      console.log("disconnected");
    };
  },

}
</script>

<style scoped>

</style>
