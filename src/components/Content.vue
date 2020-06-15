<template>
  <div class="example-content">
    <section class="hero">
      <h1><span>Keystone Financial Group</span></h1>
      <p><span>Trusted financial guidance. Built to serve you.</span></p>
      <a class="button-like" href="#">Learn More</a>
    </section>

    <section class="about">
      <p>KFG provides objective, integrated financial advice for individuals and businesses in a simple yet comprehensive approach. Having an objective, certified financial planner assist you with your plan has a significant, positive impact on outcomes. Vanguard has done extensive research on this topic.</p>

      <p>The Vanguard whitepaper is available here.</p>

      <a class="button-like" href="#">Download</a>
    </section>

    <section class="categories">
      <article 
        v-for="cat in cats" 
        class="single-cat" 
        :class="cat.class"
      >
        <div class="cat-img" :style="{ backgroundImage: 'url(' + cat.img + ')' }"></div>
        <h3>{{ cat.title }}</h3>
        <p>{{ cat.body }}</p>
      </article>
    </section>

    <section class="more">
      <h2>Asset Map & Other Tools</h2>

      <p>Nulla nec orci sit amet augue sagittis sodales sit amet et quam. Sed sed ipsum scelerisque, consequat est sed, interdum sapien. Nullam eget dolor eu erat mollis sollicitudin. Nulla consequat lectus quis orci condimentum, nec rutrum diam ullamcorper.</p>

      <img class="more-img a" v-show="theme === 'a'" src="https://i.ibb.co/nLxQJKq/a-shirt.jpg" alt="a-shirt" border="0" />
      <img class="more-img a" v-show="theme === 'b'" src="https://i.ibb.co/bRZ6rMr/b-shirt.jpg" alt="b-shirt" border="0" />
      <img class="more-img b" src="https://i.ibb.co/Qkcrd2k/office.jpg" alt="office" border="0">

    </section>
  </div>
</template>

<script>
export default {
  name: 'Content',
  props: [ 'theme' ],
  data() {
    return {
      cats: [
        {
          title: 'Budget and Savings',
          body: 'Identify spending to improve cash flows for saving.',
          class: 'budget',
          img: 'https://i.ibb.co/bKgGzfW/cat1.jpg'
        },
        {
          title: 'Employee Benefits',
          body: 'Creating attractive Health and Wellness plans for SMB owners for their employees.',
          class: 'benefits',
          img: 'https://i.ibb.co/Rg1LgGF/cat2.jpg'
        },
        {
          title: 'Education Funding',
          body: 'Effectively invest to maximize availability for financial aid.',
          class: 'funding',
          img: 'https://i.ibb.co/VYd2n9z/cat3.jpg'
        },
        {
          title: 'Insurance Services',
          body: 'Protect against risk with adequate and cost effective coverage.',
          class: 'services',
          img: 'https://i.ibb.co/7zVZ4sZ/cat4.jpg'
        },
        {
          title: 'Retirement Planning',
          body: 'Maximizing your portfolio to secure a comfortable retirement.',
          class: 'retirement',
          img: 'https://i.ibb.co/X8hvRxz/cat5.jpg'
        }
      ]
    }
  }
};
</script>

<style lang="scss">
  
  @mixin shadow {
    box-shadow: 0px 6px 10px 0px rgba(51,51,51,0.6);
  }

  .hero {
    background-image: url("https://images.unsplash.com/photo-1476989142744-32553061aca5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80");
    background-repeat: no-repeat;
    background-size: cover;
    height: 500px;
    text-align: left;
    padding: .5em;

    h1,
    p {
      span {
        display: inline-block;
        background-color: rgba(black, .6);
        padding: .25em;
      }
    }

    h1,
    p,
    a {
      font-size: 160%;
    }

    h1 {
      margin-top: 10%;
      
      span {
        font-weight: 800;
        font-size: 200%;
      }
    }

    p span {
      color: white;
    }
  }  

  .about {
    padding: 2rem 0;
    text-align: center;
    border-bottom: 10px solid;

    p {
      margin-bottom: 1rem;
      padding: 0 10%;
    }
  }

  .categories {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-content: center;
    padding: 2rem;
    background-color: white;

    article {
      @include shadow;
      min-height: 20rem;
      width: 25%;
      margin: 0 1rem 1.5rem 0;
      background-color: white;
      border-bottom: 10px solid;
      padding-bottom: .5em;

      .cat-img {
        height: 150px;
        background-repeat: no-repeat;
        background-color: #ccc;
        background-size: 100%;
      }

      h3 {
        margin-top: 2em;
        margin-bottom: 1rem;
      }

      p {
        padding: 0 1em;
      }
    }
  }

  .more {
    background-color: white;
    padding: 5em 0;

    h2 {
      margin-bottom: 2em;
    }

    p {
      padding: 0 10%;
      margin-bottom: 3em;
    }

    .more-img {
      @include shadow;
      position: relative;
      transform: rotate(-6deg);
      max-width: 450px;
      z-index: 100;
    }

    .more-img.a {
      z-index: 100;
    }

    .more-img.b {
      z-index: 10;
      transform: rotate(14deg);
      margin-left: -2em;
    }
  }
</style>
