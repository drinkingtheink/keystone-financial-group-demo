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
      <article v-for="cat in cats" :class="cat.class">
        <h3>{{ cat.title }}</h3>
        <p>{{ cat.body }}</p>
      </article>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Content',
  data() {
    return {
      cats: [
        {
          title: 'Budget and Savings',
          body: 'Identify spending to improve cash flows for saving.',
          class: 'budgt'
        },
        {
          title: 'Employee Benefits',
          body: 'Creating attractive Health and Wellness plans for SMB owners for their employees.',
          class: 'benefits'
        },
        {
          title: 'Education Funding',
          body: 'Effectively invest to maximize availability for financial aid.',
          class: 'funding'
        },
        {
          title: 'Insurance Services',
          body: 'Protect against risk with adequate and cost effective coverage.',
          class: 'services'
        },
        {
          title: 'Retirement Planning',
          body: 'Maximizing your portfolio to secure a comfortable retirement.',
          class: 'retirement'
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
      padding: 0 1rem;
      background-color: white;
      border-bottom: 10px solid;

      h3 {
        margin-top: 50%;
        margin-bottom: 1rem;
      }
    }
  }
</style>
