<template>
  <div class="team">
    <h1 class="subheading grey--text">Committe Members</h1>

    <v-container class="my-5">
      <v-layout row wrap>
        <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
          <v-card flat class="text-xs-center ma-3">
            <v-responsive class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <img :src="person.avatar" />
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading">{{ person.name }}</div>
              <div class="grey--text">{{ person.role }}</div>
            </v-card-text>
            <v-card-actions>
              <v-col cols="auto" class="text-center pl-0">
                <v-row class="flex-column ma-0 fill-height" justify="center">
                  <v-col class="px-0">
                    <v-btn icon>
                      <v-icon>fab fa-whatsapp</v-icon>
                    </v-btn>
                    <v-btn icon>
                      <v-icon>fab fa-weixin</v-icon>
                    </v-btn>
                    <v-btn icon>
                      <v-icon>fas fa-phone</v-icon>
                    </v-btn>
                  </v-col>
                </v-row>
              </v-col>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      team: [
        { name: "Member 1", role: "Web developer", avatar: "/avatar-1.png" },
        { name: "Member 2", role: "Graphic designer", avatar: "/avatar-2.png" },
        { name: "Member 3", role: "Web developer", avatar: "/avatar-3.png" },
        { name: "Member 4", role: "Web developer", avatar: "/avatar-3.png" }
      ]
    };
  }
};
</script>
 <<style scoped>
 .team{
   margin:10px;
   padding:20px;
 }
 </style>