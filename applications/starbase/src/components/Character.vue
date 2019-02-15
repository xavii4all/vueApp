<template>
    <div>
        {{character}}
    </div>
</template>

<script>
export default {
    data() {
        return {
            character: {}
        }
    },
    methods: {
        fetchCharacter() {
            let proxy = 'https://cors-anywhere.herokuapp.com/';
            fetch(proxy+'http://swapi.co/api/people', {
                method: 'GET'
            })
            .then(response => response.json())
            .then(json => this.character = json)
        }
    },
    created(){
        this.fetchCharacter()
    }
}
</script>
