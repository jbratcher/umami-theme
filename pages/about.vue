<template>
  <v-container class="py-0" fluid>
    <v-row>
      <v-col class="pa-0">
        <!-- Main Section -->
        <v-container class="pa-0" fluid>
          <v-card class="d-flex flex-column align-center pt-8" flat>
            <v-card-title
              :class="{'display-2 font-weight-bold text-center': $breakpoint.mdAndUp, 'display-1 font-weight-bold text-center': $breakpoint.smAndDown}"
            >About Us</v-card-title>
            <v-card-subtitle
              :class="{'headline font-weight-bold red--text text-center my-6': $breakpoint.mdAndUp, 'title font-weight-bold red--text text-center my-6  px-9': $breakpoint.smAndDown}"
            >We're steeped in tradition but embrace modern, delicious twists</v-card-subtitle>
            <v-card flat :width="$breakpoint.mdAndUp ? '80%' : '90vw'">
              <v-card-text
                class="body-1"
              >Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed sodales augue massa, vel sagittis sem dictum nec. Donec in tortor vitae velit ultrices venenatis. Maecenas in accumsan lectus. Vestibulum nec mi sagittis, hendrerit felis nec, sollicitudin libero. Praesent tempus urna libero, eget facilisis purus posuere sed. Quisque malesuada tincidunt arcu, et pharetra felis semper malesuada. Maecenas semper lobortis mi, vitae venenatis arcu semper tempor. Etiam imperdiet ut ligula a varius. Quisque tristique varius justo, ac iaculis lorem rutrum non. Nullam non facilisis elit. Phasellus eget mollis nisl. In suscipit quam enim, sit amet finibus sem hendrerit at. Morbi eros leo, dapibus in felis in, bibendum accumsan urna.</v-card-text>
              <v-card-text
                class="body-1"
              >Suspendisse porta, tortor at semper hendrerit, sapien quam condimentum nulla, eu tempor justo dui vel enim. Fusce id gravida erat. Ut volutpat leo eu pretium condimentum. Maecenas convallis ut magna eu posuere. Nulla volutpat molestie nisi, eu ullamcorper lorem placerat nec. Integer egestas tristique felis id tincidunt. Nunc ac accumsan nulla. Pellentesque nunc nisi, ornare in nibh sed, condimentum bibendum ex. Donec pretium augue sit amet scelerisque pretium. Phasellus et elit velit. Aliquam eu interdum nulla. Mauris accumsan rutrum tincidunt. Ut quis odio venenatis, mollis risus sit amet, congue risus. Aliquam odio ligula, pharetra ut iaculis vel, feugiat vel quam. Morbi interdum posuere molestie.</v-card-text>
              <v-card-text
                class="body-1"
              >Donec in nulla tempor, mattis sem at, interdum arcu. Fusce a purus eget purus placerat tristique quis non justo. Vestibulum ante est, dictum a ullamcorper ac, iaculis quis sem. Nam tincidunt tempus tempus. Proin pellentesque consectetur velit, iaculis tempus ipsum accumsan vitae. Vestibulum varius sed erat a efficitur. Nunc vel dolor condimentum, interdum neque sed, fringilla risus. Fusce finibus bibendum lacinia. Mauris quis orci bibendum, tempor eros ac, pretium risus. Pellentesque a tellus sit amet nibh euismod finibus sit amet elementum turpis. Fusce porta libero magna, non cursus nibh accumsan ut. Vivamus eu lorem non nisl vestibulum accumsan.</v-card-text>
              <v-card-text
                class="body-1"
              >Cras ut rutrum risus. Proin lobortis nunc leo, quis laoreet massa rutrum ac. Aliquam et diam ut nulla fringilla varius. Fusce est nunc, rhoncus in dictum a, egestas sit amet massa. Praesent id tortor eu sapien aliquam convallis nec id ex. Maecenas non lorem at arcu faucibus fermentum. Aenean eu tincidunt felis. Proin mollis est non massa tempor, at semper elit laoreet. Maecenas in magna ut nisl venenatis molestie. Morbi vel lectus eget ipsum condimentum ullamcorper. Donec a vehicula felis, at accumsan lacus. Ut vitae turpis a mi interdum pellentesque ac quis erat. Cras id odio dolor.</v-card-text>
              <v-card-text
                class="body-1"
              >Nulla pharetra, enim vitae porttitor imperdiet, neque orci luctus tortor, vitae imperdiet felis arcu non purus. Morbi pellentesque quam mauris, a ornare felis dignissim id. Duis nec urna vitae tellus varius blandit vitae consequat felis. Maecenas ullamcorper velit ut magna accumsan, vel blandit diam convallis. Donec rutrum dui imperdiet metus egestas, sit amet consectetur elit egestas. Fusce consequat mattis arcu, ac vulputate diam laoreet id. Sed justo nibh, tristique nec tempus at, luctus ac erat. Nam condimentum tempus pellentesque. Ut auctor porttitor mi in consectetur. Sed orci velit, vulputate in dictum id, laoreet sit amet urna. Maecenas euismod imperdiet nisl, ac fringilla felis pulvinar eget. Aenean consequat tortor in urna accumsan ultrices. Donec vitae neque at lacus faucibus ullamcorper.</v-card-text>
            </v-card>
          </v-card>
        </v-container>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
      ]
    }
  }
}
</script>

<style lang="scss">
</style>
