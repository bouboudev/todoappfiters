<template>
  <footer class="bg-dark text-center text-white mt-5 ">
    <!-- Grid container -->
    <div class="container p-4 mt-5">
      <!-- Section: Social media -->
      <section class="mb-4 ">
        <!-- Twitter -->
        <span data-toggle="tooltip" data-placement="left" title="Mon twitter">
          <a
            class="btn btn-danger btn-floating m-1 "
            target="_blank"
            href="https://twitter.com/intent/follow?original_referer=https%3A%2F%2Fgithub.com%2Fboubou_dev&screen_name=boubou_dev"
            role="button"
            ><i class="fab fa-twitter"></i
          ></a>
        </span>

        <!-- Linkedin -->

        <span data-toggle="tooltip" data-placement="top" title="Mon Linkedin">
          <a
            class="btn btn-danger btn-floating m-1"
            href="https://www.linkedin.com/in/bouzidkrita/"
            target="_blank"
            role="button"
            ><i class="fab fa-linkedin-in"></i
          ></a>
        </span>

        <!-- Github -->

        <span data-toggle="tooltip" data-placement="bottom" title="Mon Github">
          <a
            class="btn btn-danger btn-floating m-1"
            href="https://github.com/bouboudev "
            target="_blank"
            role="button"
            ><i class="fab fa-github"></i
          ></a>
        </span>

        <!-- Notion -->

        <span
          data-toggle="tooltip"
          data-placement="right"
          title="Candidature personnalisée Notion"
        >
          <a
            class="btn btn-danger btn-floating m-1"
            href="https://grand-bench-913.notion.site/Bonjour-c-est-Bouzid-et-je-postule-chez-Fiters-d86048069c3049dfba9643e62fc51482"
            target="_blank"
            role="button"
            ><i class="far fa-id-badge"></i
          ></a>
        </span>
      </section>

      <section class="mb-4">
        <p>
          Développement d'une Todo App dans le cadre d'un test technique.
        </p>
      </section>
      <!-- Section: Text -->
    </div>
    <!-- Grid container -->

    <!-- Copyright -->
    <div class="text-center p-3" style="background-color: rgba(0, 0, 0, 0.2);">
      © {{ currentYear }}
      <a class="text-white" target="_blank" href="https://bouzid-krita.com"
        >Bouzid KRITA</a
      >
    </div>
    <!-- Copyright -->
  </footer>
</template>

<script>
export default {
  data() {
    return {
      currentYear: new Date().getFullYear(),
    };
  },
};
</script>

<style></style>
