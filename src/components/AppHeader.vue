<template>
    <header class="d-flex justify-content-center py-3">
      <ul class="nav nav-pills">
        <li class="nav-item" v-for="item in menuItems"><router-link :to="{name: item.routeName }" class="nav-link">{{ item.label }}</router-link></li>
      </ul>
    </header>
</template>

<script>
export default{
  name: "Appheader",
  data(){
    return{
      menuItems: [
        {
          label : 'Home',
          routeName : 'home'

        },
        {
          label : 'Progetti',
          routeName : 'posts'

        },
        {
          label : 'Contattaci',
          routeName : 'contact'

        },

                 ]

    }
  
  }
}
</script>