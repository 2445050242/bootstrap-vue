<template>
  <div class="wrap">
    <b-navbar toggleable="md" type="dark" variant="info" class="fixed-top">

        <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

        <b-navbar-brand href="#">NavBar</b-navbar-brand>

        <b-collapse is-nav id="nav_collapse">

          <b-navbar-nav>
            <b-nav-item href="#">Link</b-nav-item>
            <b-nav-item href="#" disabled>Disabled</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">

            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Search"/>
              <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
            </b-nav-form>

            <b-nav-item-dropdown text="Lang" right>
              <b-dropdown-item href="#">EN</b-dropdown-item>
              <b-dropdown-item href="#">ES</b-dropdown-item>
              <b-dropdown-item href="#">RU</b-dropdown-item>
              <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown>

            <b-nav-item-dropdown right>
              <!-- Using button-content slot -->
              <template slot="button-content">
                <em>User</em>
              </template>
              <b-dropdown-item href="#">Profile</b-dropdown-item>
              <b-dropdown-item href="#">Signout</b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>

        </b-collapse>
      </b-navbar>
    <div class="content">
      <b-carousel id="carousel1"
                  style="text-shadow: 1px 1px 2px #333;"
                  controls
                  indicators
                  :interval="4000"
                  img-width="800"
                  img-height="300"
                  v-model="slide"
                  @sliding-start="onSlideStart"
                  @sliding-end="onSlideEnd"
      >

        <!-- Text slides with image -->
        <b-carousel-slide caption="First slide"
                          text="Nulla vitae elit libero, a pharetra augue mollis interdum."
                          img-src="http://via.placeholder.com/800x300"
        ></b-carousel-slide>

        <!-- Slides with custom text -->
        <b-carousel-slide img-src="http://via.placeholder.com/800x300">
          <h1>Hello world!</h1>
        </b-carousel-slide>

        <!-- Slides with image only -->
        <b-carousel-slide img-src="http://via.placeholder.com/800x300">
        </b-carousel-slide>

        <!-- Slides with img slot -->
        <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
        <b-carousel-slide>
          <img slot="img" class="d-block img-fluid w-100" src="http://via.placeholder.com/800x300" alt="image slot">
        </b-carousel-slide>

        <!-- Slide with blank fluid image to maintain slide aspect ratio -->
        <!--<b-carousel-slide caption="Blank Image" img-blank img-alt="Blank image">-->
        <!--<p>-->
        <!--Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse-->
        <!--eros felis, tincidunt a tincidunt eget, convallis vel est. Ut pellentesque-->
        <!--ut lacus vel interdum.-->
        <!--</p>-->
        <!--</b-carousel-slide>-->

      </b-carousel>
      <b-card-group deck style="margin: 1rem 0">
        <b-card img-src="https://placekitten.com/1000/300"
                img-alt="Card image"
                img-top>
          <p class="card-text">
            Some quick example text to build on the card and make up the bulk of the card's content.
          </p>
        </b-card>
        <b-card img-src="https://placekitten.com/1000/300"
                img-alt="Card image"
                img-bottom>
          <p class="card-text">
            Some quick example text to build on the card and make up the bulk of the card's content.
          </p>
        </b-card>
      </b-card-group>
      <div style="margin: 2rem 0">
        <b-media>
          <b-img slot="aside" blank blank-color="#ccc" width="64" alt="placeholder" />
          <h5 class="mt-0">Media Title</h5>
          <p>
            Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante
            sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis.
            Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis
            in faucibus.
          </p>
          <p>
            Donec sed odio dui. Nullam quis risus eget urna mollis ornare vel eu leo. Cum
            sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
          </p>
          <b-media>
            <b-img slot="aside" blank blank-color="#ccc" width="64" alt="placeholder" />
            <h5 class="mt-0">Nested Media</h5>
            <p class="mb-0">
              Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia
              congue felis in faucibus.
            </p>
          </b-media>
        </b-media>
      </div>
      <div style="margin: 2rem 0">
        <b-media>
          <b-img slot="aside" blank blank-color="#ccc" width="64" alt="placeholder" />
          <h5 class="mt-0">Media Title</h5>
          <p>
            Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante
            sollicitudin. Cras purus odio, vestibulum in vulputate at, tempus viverra turpis.
            Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia congue felis
            in faucibus.
          </p>
          <p>
            Donec sed odio dui. Nullam quis risus eget urna mollis ornare vel eu leo. Cum
            sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
          </p>
          <b-media>
            <b-img slot="aside" blank blank-color="#ccc" width="64" alt="placeholder" />
            <h5 class="mt-0">Nested Media</h5>
            <p class="mb-0">
              Fusce condimentum nunc ac nisi vulputate fringilla. Donec lacinia
              congue felis in faucibus.
            </p>
          </b-media>
        </b-media>
      </div>
    </div>
    <footer class="w-100 p-4">底部声明<br>底部声明<br></footer>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        form: {
          email: '',
          name: '',
          food: null,
          checked: [],
        },
        foods: [
          { text: 'Select One', value: null },
          'Carrots', 'Beans', 'Tomatoes', 'Corn'
        ],
        show: true,
        slide: 0,
        sliding: null
      }
    },
    methods: {
      onSubmit (evt) {
        evt.preventDefault();
        alert(JSON.stringify(this.form));
      },
      onReset (evt) {
        evt.preventDefault();
        /* Reset our form values */
        this.form.email = '';
        this.form.name = '';
        this.form.food = null;
        this.form.checked = [];
        /* Trick to reset/clear native browser form validation state */
        this.show = false;
        this.$nextTick(() => { this.show = true });
      },
      onSlideStart (slide) {
        this.sliding = true
      },
      onSlideEnd (slide) {
        this.sliding = false
      }
    }
  }
</script>
<style type="scss">
  .content{
    padding-top: 3.5rem;
  }
  footer{
    background: #17a2b8;
    color: #fff;
    line-height: 2;
    text-align: center;
  }
</style>
