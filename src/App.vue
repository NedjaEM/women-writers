<template>
  <v-app>
    <v-app-bar
      fixed
      color="#fcb69f"
      dark
      :collapse="!collapseOnScroll"
      :collapse-on-scroll="collapseOnScroll"
      height="100vh"
    >
      Women Translated from Arabic to English
    </v-app-bar>

    <template>
      <div>
        <v-container>
          <v-row>
            <v-col cols="4">
              <v-card height="10vh"> </v-card>
              <v-row no-gutters>
                <template v-for="(n, i) in writer_list">
                  <v-col :key="i">
                    <v-card
                      outlined
                      tile
                      @click.prevent="onClick(n['Title in English'])"
                    >
                      <v-img
                        width="20vh"
                        height="30vh"
                        color="gray"
                        :src="n['Book Cover']"
                      ></v-img>
                    </v-card>
                  </v-col>
                  <v-responsive
                    v-if="n === 2"
                    :key="`width-${n}`"
                    width="100%"
                  ></v-responsive>
                </template>
              </v-row>
            </v-col>
            <v-col cols="8">
              <template v-for="(n, i) in writer">
                <v-card
                  :key="i"
                  style="position: Fixed"
                  height="95%"
                  width="60%"
                  class="pa-2"
                  outlined
                  tile
                  dark
                >
                  <v-card-title class="text-right">
                    <span class="title font-weight-light">{{
                      n["Date of Translation"]
                    }}</span>
                  </v-card-title>
                  <v-list-item class="font-weight-light">
                    <v-list-item-avatar size="100" class="mb-auto">
                      <v-img :src="n['Author Image']"></v-img>
                    </v-list-item-avatar>

                    <v-list-item-content>
                      <div class="overline mb-4"></div>
                      <v-list-item-title
                        class="headline font-weight-light mb-3 text-wrap"
                        style="word-break: normal"
                        >{{ n["Title in English"] }}</v-list-item-title
                      >
                      <v-list-item-title
                        class="headline mb-1 text-wrap"
                        style="word-break: normal"
                        >{{ n["Title in Arabic"] }}</v-list-item-title
                      >
                      <div>{{ n["Description"] }}</div>

                      <v-list-item
                        >Publishing House:
                        {{ n["Publishing House"] }}</v-list-item
                      >
                      <v-list-item
                        >Translator: {{ n["Translator"] }}</v-list-item
                      >
                      <v-list-item
                        >Publication Date:
                        {{ n["Date of Translation"] }}</v-list-item
                      >
                    </v-list-item-content>
                  </v-list-item>
                  <v-card-actions>
                    <v-col justify-space-between cols="7" class="text-right">
                      <v-btn small class="btn-txt" color="#4F695E" align-left
                        >Islam</v-btn
                      >
                      <v-btn small class="btn-txt" color="#351F1A" align-left
                        >Women</v-btn
                      >

                      <v-btn small class="btn-txt" color="#41444E" align-left
                        >Religion</v-btn
                      >
                    </v-col>
                  </v-card-actions>
                </v-card>
              </template>
            </v-col>
          </v-row>
        </v-container>
      </div>
    </template></v-app
  >
</template>


<script>
import writer_list from "../src/assets/data.csv";
import writer from "../src/assets/data.csv";
export default {
  name: "App",

  components: {},

  data: () => ({
    writer_list,
    writer,
    alignments: ["grid", "card"],
    collapseOnScroll: true,
  }),

  methods: {
    onClick: function (name) {
      this.writer = writer;
      this.writer = this.writer.filter((item) => {
        if (item["Title in English"] != null) {
          return item["Title in English"] == name;
        }
      });
    },
  },
};
</script>
