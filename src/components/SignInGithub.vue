<script setup>
  import { createClient } from '@supabase/supabase-js'
  const { user, session, error } = await supabase.auth.signIn({
    provider: 'github',
  })
    
</script>
    
<template>
  <div>
    <button @click="signInWithGithub()">Login with Github</button>
    <button @click="signout()">Sign Out with Github</button>
  </div>
</template>
    
<script>

const SUPABASE_URL = 'https://ehsxahhhjirnkblciosf.supabase.co'
const SUPABASE_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImVoc3hhaGhoamlybmtibGNpb3NmIiwicm9sZSI6ImFub24iLCJpYXQiOjE2NjMzMjg5MjMsImV4cCI6MTk3ODkwNDkyM30.2zVCj9OfdyF_DADeP_r5V45DVS7X5GtX5VEE5SEU4Zg'
const supabase = createClient(SUPABASE_URL, SUPABASE_KEY)


export default {
  methods: {
    async signInWithGithub() {
      const { user, session, error } = await supabase.auth.signIn({
      provider: 'github',
      })
    },
    async signout() {
      const { error } = await supabase.auth.signOut()
    },
  }
}
</script>

<style>
@import '../assets/base.css';

header .hidden {
  visibility: hidden;
  overflow: hidden;
  display: flex;
  display: inline-block;
  place-items: flex-start;
  flex-wrap: wrap;
}

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

a,
.green {
  text-decoration: none;
  color: hsla(160, 100%, 37%, 1);
  transition: 0.4s;
}

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
    place-items: center;
  }

  #app {
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding: 0 2rem;
  }

  header {
    display: inline-block;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    display: inline-block;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
    