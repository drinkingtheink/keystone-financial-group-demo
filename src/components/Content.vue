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
          img: 'https://kfg.netlify.app/services/budget-and-savings/thumb_huc735add9cb52c8c146cf737f64caa499_1992467_99fe038172c64cf345acbb8f48e4cc81.jpg'
        },
        {
          title: 'Employee Benefits',
          body: 'Creating attractive Health and Wellness plans for SMB owners for their employees.',
          class: 'benefits',
          img: 'https://kfg.netlify.app/services/employee-benefit-design-and-implementation/thumb_hu2e061bfdbee715a9a71c24d65135fdec_435015_2897019e7775d4d80fcb8f4f6524b048.jpg'
        },
        {
          title: 'Education Funding',
          body: 'Effectively invest to maximize availability for financial aid.',
          class: 'funding',
          img: 'https://kfg.netlify.app/services/education-funding/thumb_hu6c04fd1a081859c295d8820ca09e5284_287182_680c704813aecc7331cc81ff1dc26a88.jpg'
        },
        {
          title: 'Insurance Services',
          body: 'Protect against risk with adequate and cost effective coverage.',
          class: 'services',
          img: 'https://kfg.netlify.app/services/insurance-services/thumb_hu8c4defa15d527709c2abe1551d29064c_2876026_d5bb610ca5cadce559a5c8e967d8212c.jpg'
        },
        {
          title: 'Retirement Planning',
          body: 'Maximizing your portfolio to secure a comfortable retirement.',
          class: 'retirement',
          img: 'https://kfg.netlify.app/services/retirement-and-social-security-planning/thumb_hubece55e4d000ae2db08555d5b39da967_3582779_ba773edfac1051e24b7c3ab98c259d18.jpg'
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
