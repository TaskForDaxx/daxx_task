<template>
  <div id="app">
    <HeaderSchedule/>
    <div class="blockFlexHorizontally">
      <MenuSchedule
              :title="menu.title"
              :imageLog="menu.imageLog"
              :terminalName="menu.terminalName"
              :countryCode="menu.countryCode"
              :address="menu.address"
      />

      <div class="blockFlexVertical">
        <LinkSchedule/>
        <div class="MainForSchedule">
          <MainSchedule :data="loadData"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    import HeaderSchedule from './components/HeaderSchedule'
    import LinkSchedule from './components/LinkSchedule'
    import MenuSchedule from './components/MenuSchedule'
    import MainSchedule from './components/MainSchedule'
    export default {
        name: 'app',
        props:[
            'dataOpen'
        ],
        components: {
            HeaderSchedule,
            LinkSchedule,
            MenuSchedule,
            MainSchedule
        },
        data () {

            return {
                menu: {
                    title: 'TERMINAL OVERVIEW',
                    imageLog: '../assets/logo.png',
                    terminalName: 'WEST',
                    countryCode:'NLD',
                    address:'Some address'
                },
                loadData: ''
            }
        }
    }

</script>

<style>
  #app {
    margin: 0;
    padding: 0;
  }
  .blockFlexHorizontally{
    display: flex;
  }
  .blockFlexVertical{
    width: 100%;
  }
  .MainForSchedule{
    padding: 15px 0 0 15px;
  }
</style>