<template>
<div>
  <div class="pb-0 mt-0 mb-4 border-bottom">
    <h3>Device List</h3>
  </div>

  <table class="table table-bordered table-hover" v-if="devices.length > 0">
    <thead class="thead-light">
      <tr>
        <th>UID</th>
        <th class="text-center">Version</th>
        <th class="text-center">Hardware</th>
      </tr>
    </thead>
    <tbody>
        <tr v-for="device in devices" @click="$router.push(`/devices/${device.uid}`)" :key="device.uid">
          <td>{{ device.uid }}</td>
          <td class="text-center">{{ device.version }}</td>
          <td class="text-center">{{ device.hardware }}</td>
        </tr>
    </tbody>
  </table>
  <div class="alert d-flex flex-row" v-else-if="devices.length == 0">
    <div class="col text-center">
      <i class="fas fa-list-alt fa-6x"></i>
      <div class="align-self-center ml-2">
        The device list is empty
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: "DeviceList",

  data() {
    return {
      devices: []
    };
  },

  async created() {
    this.devices = await this.getDevices();
  },

  methods: {
    async getDevices() {
      return await this.$http.get("/api/devices").then(res => {
        return res.data;
      });
    }
  },

  filters: {
    pretty(v) {
      return v.substring(0, 6) + "...";
    }
  }
};
</script>

<style scoped>
tr {
  cursor: pointer;
}

.alert {
  padding: 0;
}

.fa-list-alt {
  color: #e5e5e5;
}
</style>