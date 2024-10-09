<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-ressource')"
      :mode="storedResButtonMode"
      >Stored Ressources</base-button
    >
    <base-button
      @click="setSelectedTab('add-ressource')"
      :mode="AddResButtonMode"
      >Add Ressources</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredRessource from './StoredRessource.vue';
import AddRessource from './AddRessource.vue';
export default {
  components: {
    StoredRessource,
    AddRessource,
  },
  data() {
    return {
      selectedTab: 'stored-ressource',
      storedRessources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'the official vuejs documentattion',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google',
          link: 'https://google.com',
        },
      ],
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-ressource' ? null : 'flat';
    },
    AddResButtonMode() {
      return this.selectedTab === 'add-ressource' ? null : 'flat';
    },
  },
  provide() {
    return {
      ressources: this.storedRessources,
      addRessource: this.addRessource,
      removeRessource: this.removeRessource,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },

    addRessource(title, description, url) {
      const newRessource = {
        id: new Date().toISOString,
        title: title,
        description: description,
        link: url,
      };

      this.storedRessources.unshift(newRessource);
      this.selectedTab = 'stored-ressource';
    },

    removeRessource(resId) {
      const resIndex = this.storedRessources.findIndex(
        (res) => res.id !== resId
      );
      this.storedRessources.splice(resIndex, 1);
    },
  },
};
</script>
