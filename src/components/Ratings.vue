<template>
  <div class="rating">
    <span>
      <i
        :class="[
          ratings >= 1
            ? 'fas fa-star'
            : ratings >= 0.5
            ? 'fas fa-star-half-alt'
            : 'far fa-star',
        ]"
      />
    </span>
    <span>
      <i
        :class="[
          ratings >= 2
            ? 'fas fa-star'
            : ratings >= 1.5
            ? 'fas fa-star-half-alt'
            : 'far fa-star',
        ]"
      />
    </span>
    <span>
      <i
        :class="[
          ratings >= 3
            ? 'fas fa-star'
            : ratings >= 2.5
            ? 'fas fa-star-half-alt'
            : 'far fa-star',
        ]"
      />
    </span>
    <span>
      <i
        :class="[
          ratings >= 4
            ? 'fas fa-star'
            : ratings >= 3.5
            ? 'fas fa-star-half-alt'
            : 'far fa-star',
        ]"
      />
    </span>
    <span>
      <i
        :class="[
          ratings >= 5
            ? 'fas fa-star'
            : ratings >= 4.5
            ? 'fas fa-star-half-alt'
            : 'far fa-star',
        ]"
      />
    </span>
  </div>
</template>

<script>
export default {
  props: ["ratings"],
  name: "Ratings",
};
</script>
