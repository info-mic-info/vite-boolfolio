        <script>
export default {
  name: "AppHeader",
  data() {
    return {
      menuItems: [
        {
          label: "Homepage",
          routeName: "homepage",
          //   link: "/",
        },
        {
          label: "Blog",
          routeName: "post_list",
          //   link: "/",
        },
      ],
    };
  },
};
</script>


<template lang="">
    <header>
    <nav>
       <div class="container">
        <div class="navbar-brand">
            <img src="./img/logo.png" >
        </div>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav">
                <li class="nav-item" v-for="(item, index) in menuItems" :key="index">
                <!-- <a :href="item.link" class="nav-link">
                {{item.label}}
            </a> -->
            <router-link :to="{name: item.routeName}">{{item.label}}</router-link>
            </li>
            </ul>
        </div>
       </div> 
    </nav>
</header>
</template>

<style lang="">
</style>