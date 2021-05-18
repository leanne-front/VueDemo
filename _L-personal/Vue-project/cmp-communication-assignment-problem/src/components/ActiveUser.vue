<template>
    <li>
        <h2>{{ name }} {{ isFavorite ? "(Favorite)" : "" }} </h2>
        <button @click="toggleFavorite(id)">Favorite it</button>
        <button @click="toggleDetails">Show Details</button>
        <ul v-if="detailsAreVisible">
            <li>
                <strong>Phone:</strong>
                {{ phone }}
            </li>
            <li>
                <strong>Email:</strong>
                {{ email }}
            </li>
            <button @click="$emit('delete')">Delete</button>
        </ul>
        
    </li>
</template>

<script>
export default {
props:{
    // "friends": {
    //   type: Object
    // },
    id:{
        type:String
    }, 
    name:{
        type:String
    }, 
    phone:{
        type:String
    }, 
    email:{
        type:String
    }, 
    isFavorite:{
        type: Boolean
    }
},
data() {
    return {
    isFavoriteInApp: false,
    detailsAreVisible: false
    };
},
methods: {
    toggleDetails() {
    this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite(id) {
    this.$emit('toggleEvent', id);
    }
}
};
</script>