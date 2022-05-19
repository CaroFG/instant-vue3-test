<template>
  <ais-instant-search :search-client="searchClient" index-name="artWorks">
    <ais-search-box />
    <ais-sort-by
                    :items="[
                      { value: 'artWorks', label: 'Featured' },
                      { value: 'artWorks:DateToSortBy:asc', label: 'Date asc.' },
                      { value: 'artWorks:DateToSortBy:desc', label: 'Date desc.' }
                    ]"
                    :class-names="{
                      'ais-SortBy': 'MyCustomSortBy'
                    }"
                  />
<ais-infinite-hits>
  <template v-slot:item="{ item }">
    {{ item.Title }}
    {{ item.Date }}
  </template>
</ais-infinite-hits>

  </ais-instant-search>
</template>

<script>
import { instantMeiliSearch } from '@meilisearch/instant-meilisearch';

export default {
  data() {
    return {
      searchClient: instantMeiliSearch(
        "http://localhost:7700",
        ""
      ),
    };
  },
};
</script>

<style>
body {
  font-family: sans-serif;
  padding: 1em;
}
</style>
