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
        loadInfo: {
            let xhr = new XMLHttpRequest();
            xhr.open('GET', 'http://wb-predictivemaintenance-api.prsp7vkew2.eu-central-1.elasticbeanstalk.com/api/TorqueValues', false);
            xhr.send();
            if (xhr.status != 200) {
                // обработать ошибку
                alert('Ошибка ' + xhr.status + ': ' + xhr.statusText);
            } else {
                // let lenghtData = xhr.responseText.length;
                let a = xhr.responseText
                let b  = JSON.parse(a)

                let dataOpen = b.map(function(name) {
                    if (name.Direction == "Open") {
                        return name
                    }
                });
                console.log(dataOpen)
            }
        }
        return {
            menu: {
                title: 'TERMINAL OVERVIEW',
                imageLog: '',
                terminalName: 'WEST',
                countryCode:'NLD',
                address:'Some address'
            },
            loadData: this.dataOpen
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
