 <template>
 <transition name="fade">
    <nav class="nav" v-show="show">
      <div class="nav__image">
        <img class="nav__image-pic" src="/pics/personal/paintings/5.webp" alt="skar_picture" width="100%" height="100%" />
      </div>
      <div class="nav__links">
        <NuxtLink to="/" class="nav__links-link" rel="home">HOME</NuxtLink>
        <NuxtLink to="/personal_pass" class="nav__links-link" rel="personal_arts">PERSONAL ARTS</NuxtLink>
        <NuxtLink to="/client_pass" class="nav__links-link" rel="clients_work">CLIENTS WORK</NuxtLink>
        <NuxtLink to="/about" class="nav__links-link" rel="about">ABOUT</NuxtLink>
        <NuxtLink to="/contact" class="nav__links-link" rel="contact">CONTACT</NuxtLink>
      </div>
      <div class="socialLinks">
        <a href="https://patreon.com/skar" class="socialLinks__link"><i class="fa-brands fa-patreon"></i></a>
        <a href="https://twitter.com/elbuba_joshua" class="socialLinks__link"><i class="fa-brands fa-twitter"></i></a>
        <a href="https://instagram.com/i.am.skar" class="socialLinks__link"><i class="fa-brands fa-instagram"></i></a>
      </div>
    </nav>
 </transition>
</template>

<script>
export default {
  props: ["show", "x"]
}
</script>

<style lang="scss" scoped>
    .nav{
    background-color: $chill ;
    box-shadow: 0px 0px 5px 2px $primary;
    // width: fit-content;
    position: fixed;
    min-height: 100vh;
    padding: 2em 6vmin 0 6vmin;
    width: 40vmin;
    z-index: 4;

    &__image{
      width: 30vmin;
      height: 30vmin;
      overflow: hidden;
      border-radius: 50%;
      margin: 1em auto 0 auto;

      &-pic{
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center center;
      }

    }

    &__links{
      margin: 2.5em auto 0 auto;
      display: flex;
      flex-direction: column;
      &-link{
        color: $primary;
        font-family: "Roboto";
        font-weight: bold;
        font-size: 0.81em;
        margin: 0 0 0 0;
        letter-spacing: 0.17em;
        padding: 2vmin 0 2vmin 0;
        cursor: pointer;
        text-align: center;
        text-decoration: none;
        transition: 0.4s font-size, 0.4s color;
      
        &:hover{
            font-size: 0.9em;
          color: $opa;
        }
      
      }
    }
  }

  .fade-enter-active, .fade-leave-active {
  transition: all .4s ease;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  transform: translateX(-10vmin); 
  opacity: 0;
}


@media only screen and (max-width: 780px){
    .nav{
      width: 65vw;

      &__image{
        width: 50vw;
        height: 50vw;
      }

      &__links{

        &-link{
          font-size: 0.9em;
          padding: 4vmin 0 4vmin 0;
        }
      }
    }
}

.socialLinks{

  position: absolute;
  bottom: 15vh;
  left: 0;
  width: 100%;
  text-align: center;

  &__link{
    color: black;

     &:hover{
      color: $primary-no;
    }
    
    &:not(:first-child){
      margin: 0 0 0 1.3em;
    }

    & i{
      font-size: 1.3em;
    }
  }
}

@media only screen and (min-width: 780px){
  .socialLinks{
    bottom: 10vh;
  }
}


</style>