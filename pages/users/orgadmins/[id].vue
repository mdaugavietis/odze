<script setup>
import { ref } from 'vue'

const id  = parseInt(useRoute().params.id.toString())

const { data: user_data }  = await useFetch('/api/get_user_id',{
        method: 'POST',
        body: {
            id: id
        }
    })

const { data: org_data}  = await useFetch('/api/get_org_id',{
        method: 'POST',
        body: {
            id: user_data.value.user.orgId 
        }
    })


</script>

<template>
            <p>{{ user_data?.user?.email }}</p>
    <p>{{ org_data?.organization.name}}</p>

</template>