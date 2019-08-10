<template>
  <section class="search">
    <h1>查询玩家信息/Track Player Stats</h1>
    <form v-on:submit.prevent="onSubmit">
      <div class="form-group">
        <label for="platform">平台/Platform</label>
        <select name="platform" id="platform" v-model="platform">
          <option value="steam">Steam</option>
        
        </select>
      </div>
      <div class="form-group">
        <label for="gamertag">用户名/Gamertag</label>
        <input
          type="text"
          name="text"
          v-model="gamertag"
          id="gamertag"
          placeholder="steam id, csgo id etc"
        />
      </div>
      <div class="form-group">
        <input type="submit" value="查找/Search" class="btn" />
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      platform: "steam",
      gamertag: ""
    };
  },
  beforeCreate() {
    document.body.className = "body-bg-image";
  },
  methods: {
    onSubmit() {
      if (!this.gamertag) {
        this.$toasted.show("输入Steam id/Please enter a gamertag", {
          duration: 3000,
          icon: "exclamation-circle"
        });
      } else {
        this.$router.push(`/profile/${this.platform}/${this.gamertag}`);
      }
    }
  }
};
</script>

<style>
</style>
