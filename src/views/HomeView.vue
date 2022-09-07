<template>
  <div class="grid">
    <main>
      <section>
        <h1>Resume</h1>
        <h2>Haloo, {{ name }}</h2>
        <p>
          {{ description }}
        </p>
      </section>
      <section id="section-1">
        <h2>Experience</h2>
        <ol>
          <li v-for="(item, index) in experience" :key="item.id">
            <h3>{{ item.title }}</h3>
            <h4>
              {{ item.year }} |
              <span @click="changeCheck(index, 'experience')">detail</span>
            </h4>
            <p v-if="item.checkDescription === true">
              {{ item.description }}
            </p>
          </li>
        </ol>
        <h2>Education</h2>
        <ol>
          <li v-for="(item, index) in education" :key="item.id">
            <h3>{{ item.title }}</h3>
            <h4>
              {{ item.year }} |
              <span @click="changeCheck(index, 'education')">detail</span>
            </h4>
            <p v-if="item.checkDescription === true">
              {{ item.description }}
            </p>
          </li>
        </ol>
      </section>
      <section id="section-2">
        <h2>Skills</h2>
        <ul>
          <li v-for="skill in skills" :key="skill.id">
            <div>
              <h3>{{ skill.name }}</h3>
              <div
                class="bar-percentage"
                :style="{ width: skill.percentage + '%' }"
              >
                <p>{{ skill.percentage }} %</p>
              </div>
            </div>
          </li>
        </ul>
      </section>
      <section id="section-3">
        <form @submit.prevent="alertNotif" ref="formReset">
          <h2>Contact Us</h2>
          <p>Name:</p>
          <input
            v-model="form.base.name"
            placeholder="Masukkan nama"
            required
          />
          <p>Email:</p>
          <input
            v-model="form.base.email"
            placeholder="Masukkan email"
            required
          /><br />
          <p>Note:</p>
          <textarea
            v-model="form.base.note"
            placeholder="add multiple lines"
            required
          ></textarea>
          <br />
          <button type="submit">Submit</button>
        </form>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Rakhel Cakra Kusumadinata Sera",
      description:
        "Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum deleniti inventore nemo dolorem quas consequatur natus amet velit. Aperiam maiores, veniam iure accusamus repellat cupiditate et enim omnis blanditiis labore!",
      experience: [
        {
          id: 1,
          title: "Kerja wkwk",
          year: "2019-2020",
          description: "lorem ekrnknksnfksnfk amkfmakdfknaldkk",
          checkDescription: false,
        },
        {
          id: 1,
          title: "Kerja wkwk",
          year: "2019-2020",
          description: "lorem ekrnknksnfksnfk amkfmakdfknaldkk",
          checkDescription: false,
        },
        {
          id: 1,
          title: "Kerja wkwk",
          year: "2019-2020",
          description: "lorem ekrnknksnfksnfk amkfmakdfknaldkk",
          checkDescription: false,
        },
      ],
      education: [
        {
          id: 1,
          title: "Kerja wkwk",
          year: "2019-2020",
          description: "lorem ekrnknksnfksnfk amkfmakdfknaldkk",
          checkDescription: false,
        },
        {
          id: 1,
          title: "Kerja wkwk",
          year: "2019-2020",
          description: "lorem ekrnknksnfksnfk amkfmakdfknaldkk",
          checkDescription: false,
        },
      ],
      skills: [
        {
          id: 1,
          name: "HTML",
          percentage: 90,
        },
      ],
      form: {
        base: {
          name: "",
          email: "",
          note: "",
        },
        baseReset: {
          name: "",
          email: "",
          note: "",
        },
        error: {
          name: "",
          email: "",
        },
      },
    };
  },
  methods: {
    changeCheck(indexLocation, name) {
      // if (name === "experience") {
      //   this.experience[indexLocation].checkDescription =
      //     !this.experience[indexLocation].checkDescription;
      // } else if (name === "education") {
      //   this.education[indexLocation].checkDescription =
      //     !this.education[indexLocation].checkDescription;
      // }
      this[name][indexLocation].checkDescription =
        !this[name][indexLocation].checkDescription;
    },
    alertNotif() {
      alert(
        `Thank You ${this.form.base.name}, we'll send you an email to ${this.form.base.email} regarding ${this.form.base.note}`
      );
      this.$refs.formReset.reset();
      this.form.base = this.form.baseReset;
      console.info(
        `Thank You ${this.form.base.name}, we'll send you an email to ${this.form.base.email} regarding ${this.form.base.note}`
      );
    },
  },
};
</script>

<style scoped>
.grid {
  display: grid;
  place-items: center;
}
main {
  background-color: #b9fff8;
  max-width: 50%;
  margin: 30px 0;
  padding-left: 20px;
}
.bar-percentage {
  background-color: blue;
  height: 25px;
  width: 50%;
  border-radius: 20px;
}
.bar-percentage p {
  text-align: center;
  padding-top: 2.5px;
  margin: 20px;
  color: aliceblue;
}

button {
  margin-top: 15px;
}

section {
  margin-bottom: 20px;
}
</style>
