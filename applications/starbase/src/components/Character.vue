<template>
    <div>
        {{character}}
    </div>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            character: {}
        }
    },
    methods: {
        fetchCharacter(id) {
            let proxy = 'https://cors-anywhere.herokuapp.com/';
            fetch(proxy+`http://swapi.co/api/people/${id}`, {
                method: 'GET'
            })
            .then(response => response.json())
            .then(json => this.character = json)
        }
    },
    created(){
        this.fetchCharacter(this.id)
    }
}
</script>
