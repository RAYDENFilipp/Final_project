<script>
  import Footer from "../Footer/Footer.svelte";
</script>

<style>
  [id="contacts"] {
    height: inherit;
    overflow: auto;
  }

  iframe {
    height: 63vh;
    width: inherit;
  }
</style>

<div id="contacts">
  <div class="container w-100">
    <article class="row justify-content-around align-items-center">
      <!-- Contacts info -->
      <section class="col-8 pt-4">
        <h2 class="text-uppercase text-center w-40">Find us</h2>
        <p class="h5 mb-0 w-40">
          Solomianska St, 7,
          <br />
          Kyiv, 03110
        </p>
        <br />
        <a
          class="btn btn-info btn-social mx-1"
          href="https://www.facebook.com/"
          target="_blank"
          aria-label="Visit us at Facebook"
          rel="noreferrer">
          <i class="fab fa-facebook-f" />
        </a>
        <a
          class="btn btn-info btn-social mx-1"
          href="https://twitter.com/?lang=en"
          target="_blank"
          aria-label="Visit us at Twitter"
          rel="noreferrer">
          <i class="fab fa-twitter" />
        </a>
        <a
          class="btn btn-info btn-social mx-1"
          href="https://www.linkedin.com/"
          target="_blank"
          aria-label="Visit us at Linked-In"
          rel="noreferrer">
          <i class="fab fa-linkedin-in" />
        </a>
      </section>

      <!-- Map -->
      <div class="row col-12 pb-3 mt-3">
        <iframe
          class="border-0 mx-auto w-md-50"
          title="State University of Telecommunications on the map"
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d12090.613512847922!2d30.46984709125832!3d50.4273456508177!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x638e8cfbdbe5fddc!2sState+University+of+Telecommunications!5e0!3m2!1sen!2sua!4v1564161731057!5m2!1sen!2sua"
          allowfullscreen />
      </div>
    </article>
  </div>
  <Footer />
</div>
