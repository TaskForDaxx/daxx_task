<template>
    <div class="MenuSchedule">
        <div class="title">
            <span class="glyphicon glyphicon-chevron-left spanTitleMarRig"></span>
            {{title}}
            <span class="glyphicon glyphicon-th-list spanTitleMarLeft"></span>
        </div>
        <div>
            <img src='../assets/logo.png'/>
        </div>
        <div class="descreprion">
            <div class="descrDiv">
                <span>terminalName:</span><br>
                <span class="descriprionIN">{{terminalName}}</span>
            </div>
            <div>
                <span >countryCode:</span><br>
                <span class="descriprionIN">{{countryCode}}</span>
            </div>
            <div>
                <span >address:</span><br>
                <span class="descriprionIN">{{address}}</span>
            </div>
        </div>

    </div>
</template>

<script>
    import "bootstrap"


    export default {
        name: "menu-schedule",
        props:[
            'title',
            'imageLog',
            'terminalName',
            'countryCode',
            'address'
        ]
    }
</script>

<style scoped>
    .MenuSchedule{
        height: calc(100vh - 80px);
        min-height: 410px;
        width: 20%;
        background: #fff;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
    }
    .title{
        height: 30px;
        width: 100%;
        background: #7191fb;
        font-size: 16px;
        color: #fff;
        line-height: 30px;
        /*display: flex;*/
    }
    .spanTitleMarRig{
        margin-right: 5px;
        margin-left: 5px;
    }
    .spanTitleMarLeft{
        margin-left: 5px;
    }
    .descreprion{
        padding: 15px 0 0 15px;
    }
    .descriprionIN{
        font-size: 14px;
        font-style: unset;
        color: #000;
    }
    .descrDiv{
        margin-bottom: 5px;
    }
    img{
        width: 240px;
        height: 240px;
    }
</style>