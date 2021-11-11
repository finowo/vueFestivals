<template>
  <b-col>
    <h2>Festivals Show Page</h2>
    <p>{{ festival.title }}</p>
    <p>{{ festival.description }}</p>
  </b-col>
</template>

<script>
import axios from "axios";

export default {
  name: "FestivalsShow",
  components: {},
  data() {
    return { festival: [] };
  },
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
      axios
        .get(
          `https://festivals-api.herokuapp.com/api/festivals/${this.$route.params.id}`,
          {
            headers: {
              Authorisation:
                "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFkbWluQGZlc3RpdmFscy5pZSIsIl9pZCI6IjYxODAzYTMxNGM2OTczOGEyMGQxOTMyMyIsImlhdCI6MTYzNjYzMDY3OH0.dAXrsD28Qi4mVMUpNSiIQTzTUIg6m2kRT5xdfr0LinY",
            },
          }
        )
        .then((response) => {
          console.log(response);
          this.festival = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
