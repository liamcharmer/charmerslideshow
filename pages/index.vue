<template>
  <div>
    <h1>Website title</h1>
    <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nemo nobis eveniet ipsa nisi eligendi dolorum consequuntur ab quas dolor eos officiis earum doloremque repellat non, ratione repudiandae doloribus laboriosam. Dolores!</p>

    <CharmerSlideShow :slides="slidesToPass" />
  </div>
</template>

<script>
import CharmerSlideShow from "~/components/CharmerSlideShow";

export default {
  components: { CharmerSlideShow },
  data: function() {
    return {
      slidesToPass: [
        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1556568543-a0c779b827b4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2100&q=80"
        },

        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1542489294-52dcedbce910?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80"
        },

        {
          type: "text",
          content: "This was created on live stream"
        },
        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1545863179-763ea1f70b3b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2104&q=80"
        },
        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1556568543-a0c779b827b4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2100&q=80"
        },

        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1542489294-52dcedbce910?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80"
        },

        {
          type: "text",
          content: "This was created on live stream"
        },
        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1545863179-763ea1f70b3b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2104&q=80"
        },
        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1556568543-a0c779b827b4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2100&q=80"
        },

        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1542489294-52dcedbce910?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80"
        },

        {
          type: "text",
          content: "This was created on live stream"
        },
        {
          type: "image",
          content:
            "https://images.unsplash.com/photo-1545863179-763ea1f70b3b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2104&q=80"
        }
      ]
    };
  }
};
</script>

<style>
</style>
