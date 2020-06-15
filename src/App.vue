<template>
  <div id="app" :class="theme">
    <section class="toolbar">
        <button class="a" v-on:click="clearTheme" v-show="theme">
          Clear
        </button>

        <button 
          class="toolbar-action" 
          v-on:click="updateTheme('a')"
          :class="{ active: theme === 'a' }"
        >
          Option A
        </button>

        <button 
          class="toolbar-action" 
          v-on:click="updateTheme('b')"
          :class="{ active: theme === 'b' }"
        >
          Option B
        </button>
      </section>
    </section>

    <header v-show="theme" :class="theme">
      <KFGLogo class="header-logo" />

      <div class="nav-link">
        Services
      </div>

      <div class="nav-link">
        About
      </div>
    </header>

    <section class="intro" v-show="!theme">
      <h2>Welcome Keystone Financial Group</h2>
      <KFGLogo class="intro-logo" />
      <p>Please click on an option below to see an example experience with your new logo implemented with a color palette:</p>

      <section class="option-selection">
        <button class="a" v-on:click="updateTheme('a')">
          A
        </button>

        <button class="b" v-on:click="updateTheme('b')">
          B
        </button>
      </section>
    </section>

    <Content :class="theme" :theme="theme" v-if="theme"/>
  </div>
</template>

<script>
  import Content from './components/Content.vue'
  import KFGLogo from './components/KFGLogo.vue'

  export default {
    name: 'App',
    components: {
      Content,
      KFGLogo
    },
    data() {
      return {
        theme: null
      }
    },
    methods: {
      updateTheme(themeName) {
        this.theme = themeName;
      },
      clearTheme () {
        this.theme = null;
      }
    }
  };
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Capriola&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Cantarell&display=swap');

  $p1color1: #75c394;
  $p1color2: #12361f;
  $p1color3: #568d6c;

  $p2color1: #0d2946;
  $p2color2: #2a9cd7;
  $p2color3: #40ae49;

  @mixin shadow {
    box-shadow: 0px 10px 15px 0px rgba(51,51,51,0.6);
  }

  html,
  body {
    margin: 0;
    padding: 0;
    font-size: 12pt;
  }

  h1,
  h2,
  h3,
  h4,
  h5 {
    padding: 0;
    margin: 0;
    font-family: 'Capriola', sans-serif;
  }

  p {
    margin: 0;
    padding: 0;
  }

  span,
  a,
  p,
  li {
    font-family: 'Cantarell', sans-serif;
  }

  a {
    text-transform: uppercase;
    padding: 1rem 1.5rem;
    border-radius: 5px;
    text-decoration: none;
    display: inline-block;
    margin-top: .5rem;
    transition: all .2s;

    &.button-like {
      @include shadow;

      &:hover {
        background-color: white !important;
      }
    }
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;

    > * {
      transition: all .2s;
    }

    &.a {
      .button-like:hover {
        color: $p1color3 !important;
      }
    }

    &.b {
      .button-like:hover {
        color: $p2color3 !important;
      }
    }
  }

  $toolbarHeight: 25px;

  .toolbar {
    height: $toolbarHeight;
    position: fixed;
    width: 100%;
    top: 0px;
    background-color: rgba(black, .8);  
    z-index: 1000000000;
  }

  .toolbar-action {
    &:hover {
      cursor: pointer;
    }
  }

  .toolbar-action.active {
    background-color: black;
    color: white;
    border-radius: 5px;
  }

  .option-selection {
    display: flex;
    align-content: center;
    justify-content: center;
    padding-top: 2em;

    button {
      font-size: 150%;
      padding: 5%;
      border-radius: 10px;
      margin-right: 1em;
      opacity: .8;
      background-color: rgba(black, .4);

      &:hover {
        cursor: pointer;
        opacity: 1;
      }
    }
  }

  header {
    @include shadow;
    display: flex;
    height: 65px;
    margin-top: $toolbarHeight;
    border-bottom: 5px solid;

    .header-logo {
      width: 250px
    }

    .nav-link {
      padding: 23px .5rem 0 .5rem;
      color: white;

      &:hover {
        cursor: pointer;
      }
    }

    &.a {
      background-color: $p1color1;
      border-color: $p1color3;

      .header-logo {

        > * {
          fill: $p1color2;
        }

        .leaf {
          fill: white;
        }
      }

      .nav-link {
        color: $p1color2;

        &:hover {
          color: white;
        }
      }
    }

    &.b {
      background-color: $p2color1;
      border-color: $p2color2;

      .header-logo {
        > * {
          fill: white;
        }

        .leaf {
          fill: $p2color3;
        }
      }

      .nav-link {
        color: $p2color3;

        &:hover {
          color: white;
        }
      }
    }
  }

  .intro {
    padding-top: 3em;
  }

  .intro-logo {
    max-width: 600px;
  }

  .hero {
    h1 span {
      font-family: 'Capriola', sans-serif;
    }
  }

  .example-content {
    &.a {
      background-color: $p1color1;

      p {
        color: $p1color2;
      }

      a {
        background-color: $p1color2;
        color: white;
      }

      .hero {
        h1 span {
          color: $p1color1;
        }
      }

      .about {
        border-color: $p1color3;
      }

      .categories {
        background-color: #ffffff;
        background-image: url("data:image/svg+xml,%3Csvg width='100' height='20' viewBox='0 0 100 20' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M21.184 20c.357-.13.72-.264 1.088-.402l1.768-.661C33.64 15.347 39.647 14 50 14c10.271 0 15.362 1.222 24.629 4.928.955.383 1.869.74 2.75 1.072h6.225c-2.51-.73-5.139-1.691-8.233-2.928C65.888 13.278 60.562 12 50 12c-10.626 0-16.855 1.397-26.66 5.063l-1.767.662c-2.475.923-4.66 1.674-6.724 2.275h6.335zm0-20C13.258 2.892 8.077 4 0 4V2c5.744 0 9.951-.574 14.85-2h6.334zM77.38 0C85.239 2.966 90.502 4 100 4V2c-6.842 0-11.386-.542-16.396-2h-6.225zM0 14c8.44 0 13.718-1.21 22.272-4.402l1.768-.661C33.64 5.347 39.647 4 50 4c10.271 0 15.362 1.222 24.629 4.928C84.112 12.722 89.438 14 100 14v-2c-10.271 0-15.362-1.222-24.629-4.928C65.888 3.278 60.562 2 50 2 39.374 2 33.145 3.397 23.34 7.063l-1.767.662C13.223 10.84 8.163 12 0 12v2z' fill='%2375c394' fill-opacity='0.2' fill-rule='evenodd'/%3E%3C/svg%3E");

        article {
          border-color: $p1color1;
        }
      }

      .more {
        .more-img.a {
          border: 10px solid $p1color2;
        }

        .more-img.b {
          border: 15px solid $p1color1;
        }
      }
    }

    &.b {
      background-color: $p2color2;

      p {
        color: $p2color1;
      }

      a {
        background-color: $p2color3;
        color: white;
      }

      .hero {
        h1 span {
          color: $p2color2;
        }
      }

      .about {
        border-color: $p2color1;
      }

      .categories {
        background-color: #ffffff;
        background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100' viewBox='0 0 100 100'%3E%3Cg fill-rule='evenodd'%3E%3Cg fill='%2340ae49' fill-opacity='0.26'%3E%3Cpath opacity='.5' d='M96 95h4v1h-4v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9zm-1 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9z'/%3E%3Cpath d='M6 5V0H5v5H0v1h5v94h1V6h94V5H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");

        article {
          border-color: $p2color3;
        }
      }

      .more {
        .more-img.a {
          border: 10px solid $p2color3;
        }

        .more-img.b {
          border: 15px solid $p2color2;
        }
      }
    }
  }

  .more-img {

  }
</style>
