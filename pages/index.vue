<template>
  <div class="h-full w-full">
    <ais-instant-search
      :search-client="searchClient"
      :index-name="algoliaIndex"
    >
      <mj-map />
    </ais-instant-search>
  </div>
</template>
<script>
import MjMap from "~/components/Map.vue";
import algoliasearch from "algoliasearch/lite";
import { AisInstantSearch } from "vue-instantsearch";

const ALGOLIA_APP_ID = "<insert-app-here>";
const ALGOLIA_SEARCH_ONLY_API_KEY = "<insert-key-here>";
const ALGOLIA_INDEX_NAME = "breakfast_restaurant";

const algoliaClient = algoliasearch(
  ALGOLIA_APP_ID,
  ALGOLIA_SEARCH_ONLY_API_KEY
);

export default {
  components: {
    MjMap,
    AisInstantSearch
  },
  data() {
    return {
      algoliaIndex: ALGOLIA_INDEX_NAME,
      searchClient: algoliaClient
    };
  }
};
</script>
