<template>
  <div class="main-container">
    <section class="cover imagebg height-82 text-left" data-overlay="7">
      <div class="background-image-holder"></div>
      <div class="container pos-vertical-center">
        <div class="row">
          <div class="col-sm-8">
            <h1>The Mental Care Foundation</h1>
            <div class="mb-10 typed-headline">
              <span class="h4 inline-block" style="line-height: 2em">
                We bring together technology and emotional support to give mental health a voice in
                Nigeria, where depression is seen as a “white man” illness
              </span>
            </div>
            <a class="btn btn--primary type--uppercase" href="#more">
              <span class="btn__text">Get Started</span>
            </a>
          </div>
        </div>
        <!--end of row-->
      </div>
      <!--end of container-->
    </section>
    <section class="space--xs">
      <div class="container">
        <h2 class="text-center type--uppercase">Meet The Team</h2>
        <div class="row">
          <div v-for="member in team" :key="member.id" class="col-xs-6 col-sm-4 col-lg-3">
            <div class="text-center feature">
              <div class="team-img">
                <!-- <img alt="Image" v-if="member.profilePicture == null" src="~/assets/static/img/avatar.jpg" class="avatar"/> -->
                <img alt="Image" :src="member.fields.profilePicture.fields.file.url" class="avatar"/>
              </div>
                <h4 class="type--capitalize">
                  <strong>{{member.fields.name}}</strong>
                </h4>
                <p class="mb-0 type--capitalize">{{member.fields.position}}</p>
                <a class="lead text-underline" :href="member.fields.biourl" target="_blank">
                  Bio
                </a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import {createClient} from '~/plugins/contentful.js'

const client = createClient()

export default {
  asyncData ({env}) {
    return client.getEntries({
          'content_type': env.CTF_TEAM_TYPE_ID,
        }).then(
          team => {
          // return data that should be available
          // in the template
          return {
            team: team.items
          }
        })
    }
}
</script>


