<template>
  <Header fixed>
    <SidebarToggler class="d-lg-none" display="md" mobile></SidebarToggler>
    <a class="navbar-brand" :href="$app.homePath" target="_blank">
      <img class="navbar-brand-full" src="../../../sass/vendor/tabler/brand/logo.png" height="30" alt="Doika-logo">
      <img class="navbar-brand-minimized" src="../../../sass/vendor/tabler/brand/logo-symbol.png" width="30" height="30" alt="Doika-logo">
    </a>
    <SidebarToggler class="d-md-down-none" display="lg"></SidebarToggler>
    <b-navbar-nav class="ml-auto">
      <HeaderDropdown right class="px-3 d-none d-md-block">
        <template slot="header">
          <span class="d-md-down-none">
            <i class="fe fe-plus-circle"></i>&nbsp;&nbsp;{{ $t('labels.admin.newMenu.header') }}
          </span>
        </template>
        <template slot="dropdown">
          <b-dropdown-item to="/campaigns/create" v-if="this.$app.user.can('create campaign')">
            <i class="fe fe-book"></i>&nbsp;&nbsp;{{ $t('labels.admin.newMenu.campaign') }}
          </b-dropdown-item>
          <b-dropdown-item to="/users/create" v-if="this.$app.user.can('create user')">
            <i class="fe fe-users"></i>&nbsp;&nbsp;{{ $t('labels.admin.newMenu.user') }}
          </b-dropdown-item>
        </template>
      </HeaderDropdown>
      <HeaderDropdown right class="px-3 d-none d-md-block">
        <template slot="header">
          <span class="d-md-down-none">{{ $t('labels.admin.languageMenu.header') }}</span>
        </template>
        <template slot="dropdown">
          <b-dropdown-item :key="index" v-for="(locale, index) in this.$app.locales"
                           :hreflang="index"
                           :href="`/${index}/${$app.adminPathName}${$route.fullPath}`"
          >
            {{ locale.native }}
          </b-dropdown-item>
        </template>
      </HeaderDropdown>
      <HeaderDropdown right class="px-3">
        <template slot="header">
          <img :src="this.$app.user.avatar" class="img-avatar" :alt="$t('labels.admin.accountMenu.avatar')">
          <span class="d-md-down-none">
            {{ this.$app.user.name }}
          </span>
        </template>
        <template slot="dropdown">
          <!--<b-dropdown-item :href="$app.route('user.account')">
            <i class="fe fe-user"></i>&nbsp;&nbsp;{{ $t('labels.admin.accountMenu.header') }}
          </b-dropdown-item>-->
          <b-dropdown-item :href="$app.route('admin.logout')">
            <i class="fe fe-log-out"></i>&nbsp;&nbsp;{{ $t('labels.admin.accountMenu.logout') }}
          </b-dropdown-item>
        </template>
      </HeaderDropdown>
    </b-navbar-nav>
  </Header>
</template>

<script>
export default {
  name: 'AppHeader'
}
</script>
