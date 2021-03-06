<template>
  <div>
    <div class="fixed-header">
      <TopBar />
    </div>

    <div class="page-body">
      <Breadcrumb />
      <div class="content" v-if="$page.frontmatter.component">
        <component :is="$page.frontmatter.component" />
      </div>
      <div class="content" v-else>
        <div class="content--container">
          <div class="tree-nav">
            <Sidebar :sidebarActive="treeNavOpen" />
          </div>
          <div class="content-area">
            <PageTitle />
            <MobileOnThisPage />
            <ContentPage />
            <div class="edit-on-github">
              <span class='fa fa-github'></span>
              <span>
                <a v-if=editLink
                   id="edit-link"
                   :href="editLink"
                   target="_blank"
                   rel="noopener noreferrer"
                   data-proofer-ignore
                >{{ editLinkText }}</a>
              </span>
            </div>
          </div>
          <div class="on-this-page">
            <OnThisPage />
          </div>
        </div>
      </div>
    </div>

    <Footer />

  </div>
</template>

<script>

export const LAYOUT_CONSTANTS = {
  HEADER_TO_CONTENT_GAP: 45, //px
};
export const endingSlashRE = /\/$/
export default {
  components: {
    TopBar: () => import('../components/TopBar.vue'),
    Sidebar: () => import('../components/Sidebar.vue'),
    OnThisPage: () => import('../components/OnThisPage.vue'),
    MobileOnThisPage: () => import('../components/MobileOnThisPage.vue'),
    PageTitle: () => import('../components/PageTitle.vue'),
    Breadcrumb: () => import('../components/Breadcrumb.vue'),
    ContentPage: () => import('../components/ContentPage.vue'),
    Footer: () => import('../components/Footer.vue'),
    Documentation: () => import('../components/Documentation.vue'),
    Reference: () => import('../components/Reference.vue'),
    Quickstart: () => import('../components/Quickstart.vue'),
  },
  data() {
    return {
      treeNavOpen: false
    }
  },
  mounted() {
    let that = this;
    this.$on('toggle-tree-nav', event => {
      that.treeNavOpen = event.treeNavOpen;
    });

    this.redirIfRequired();
  },
  watch: {
    $route(to, from) {
      this.redirIfRequired();
    }
  },
  computed: {
    editLink () {
      if (this.$page.frontmatter.editLink === false) {
        return
      }
      const {
        repo,
        editLinks,
        docsDir = '',
        docsBranch = 'master',
        docsRepo = repo
      } = this.$site.themeConfig.editLink
      if (docsRepo && editLinks && this.$page.relativePath) {
        console.log('page: ', this.$page)
        return this.createEditLink(repo, docsRepo, docsDir, docsBranch, this.$page.relativePath)
      }
    },
    editLinkText () {
      return (
        this.$site.themeConfig.editLink.editLinkText
        || `Edit this page`
      )
    }
  },
  methods: {
    redirIfRequired() {
      if(this.$page && this.$page.redir) {
        let anchor = window.location.href.split('#')[1] || '';
        if(anchor) {
          this.$router.replace({ path: `${this.$page.redir}#${anchor}` });
        } else {
          this.$router.replace({ path: `${this.$page.redir}` });
        }
      }
    },
    createEditLink (repo, docsRepo, docsDir, docsBranch, path) {
      return (
        `https://github.com/${docsRepo}`
        + `/edit`
        + `/${docsBranch}/`
        + (docsDir ? docsDir.replace(endingSlashRE, '') : '')
        + '/'
        + path
      )
    }
  }
}
</script>

<style lang="scss">
@import '../assets/css/prose';
</style>
