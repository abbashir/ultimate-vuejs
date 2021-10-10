<template>
  <div class="container">
    <form @submit.prevent="handleSignup">
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">Email address</label>
        <input type="email" class="form-control" v-model="email" />
      </div>

      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label"
          > password</label
        >
        <input type="password" class="form-control" v-model="password" />
        <div class="form-text text-danger" v-if="passwordError">{{ passwordError }}</div>
      </div>

      <select class="form-select mb-3" v-model="role">
        <option selected>Open this select menu</option>
        <option value="Developer">Developer</option>
        <option value="Deginer">Deginer</option>
        <option value="Manager">Manager</option>
      </select>

      <div class="mb-3">
        <label class="form-label">Skill</label>
        <input
          type="text"
          class="form-control"
          v-model="tempSkill"
          @keyup="addSkill"
        />
      </div>
      <div v-for="skill in skills" :key="skill">
        <span class="skill" @click="deleteSkill(skill)">{{ skill }}</span>
      </div>

      <div class="mb-3 form-check">
        <input type="checkbox" class="form-check-input" v-model="terms" />
        <label class="form-check-label">ACCEPT TURMS AND CONDITION</label>
      </div>
      <button type="submit" class="btn btn-primary" :disabled="!terms">Submit</button>

    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      tempSkill: "",
      skills: [],
      passwordError: ''
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = "";
      }
    },
    deleteSkill(skill){
      this.skills = this.skills.filter((item) => {
        return skill !== item
      })
    },
    handleSignup(){
      // password validation
      this.passwordError = this.password > 5 ? '' : 'password must be at least 6 character'
      if(!this.passwordError){
        console.log(this.email)
      }

    }
  },
};
</script>

<style>
.skill{
  background: gray;
  padding: 2px;
  color: wheat;
  float: left;
  display: inline;
  margin-right: 5px;
}
</style>