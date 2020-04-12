<template>
    <div>
        <hr class="divider" />
        <div>
            <table class="detail table table-bordered">
                <tbody>
                    <tr class="active">
                        <td>no</td>
                        <td>{{contact.no}}</td>
                    </tr>
                    <tr class="active">
                        <td>name</td>
                        <td>{{contact.name}}</td>
                    </tr>
                    <tr class="active">
                        <td>tel</td>
                        <td>{{contact.tel}}</td>
                    </tr>
                    <tr class="active">
                        <td>address</td>
                        <td>{{contact.address}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Constant from '~/constant'

export default {
    name : "contactbyno",
    computed : mapGetters({
        contact : 'getContactOne'
    }),
    created : function(){
        var no = this.$route.params.no;
        this.$store.commit(Constant.CHANGE_NO, {no: no})
    },
    beforeRouteUpdate(to, from, next){
        var no = to.params.no;
        this.$store.commit(Constant.CHANGE_NO, {no: no})
        next()
    }
}
</script>

<style>
table.detail { width :400px; }
</style>

