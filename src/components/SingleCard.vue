<script>
export default {
    name: "SingleCard",
    props: ['info'],
    methods: {
        bandiereDalSito(x) {
            //ESEMPIO DI BANDIERA ---->   https://flagsapi.com/ZA/shiny/64.png

            if (x == 'en') {
                x = 'gb'
            } else if (x == 'ko') {
                x = 'kr'
            } else if (x == 'ja') {
                x = 'jp'
            }

            let upperX = x.toUpperCase();
            console.log(upperX)
            return `https://flagsapi.com/${upperX}/shiny/64.png`

        },
        funzioneTitolo() {
            if (this.info.original_title) {
                return this.info.original_title
            } else {
                return this.info.original_name
            }
        },
        funzioneIMG() {
            if (this.info.poster_path) {
                return `https://image.tmdb.org/t/p/w342/${this.info.poster_path}`
            } else if (this.info.poster_path == null) {
                return '../../public/img/errore-404.jpg'
            }
        },
        funzioneVoto() {
            return Math.ceil(this.info.vote_average / 2)
        },
        funzioneTitoloTradotto() {
            if (this.info.title) {
                return this.info.title
            } else {
                return this.info.name
            }
        }
    }
}
</script>

<template>
    <div class="card my-3">
        <img :src="funzioneIMG()" class="card-img-top" :alt="funzioneTitolo()">
        <div class="card-body d-none">
            <h5 class="card-title">{{ funzioneTitolo() }}</h5>
            <h6>{{ funzioneTitoloTradotto() }}</h6>
            <div class="flag">
                <span>Original Language:</span>
                <img :src="bandiereDalSito(info.original_language)" alt="">
            </div>
            <div class="star-div">
                <span>Recensioni: </span>
                <i v-for="n in 5" class="fa-star" :class="(n <= funzioneVoto()) ? 'fa-solid' : 'fa-regular'"></i>
            </div>

        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    width: 20%;
    position: relative;

    img {
        height: 331px;
    }

    .star-div {
        margin-top: 10px;

        i {
            color: gold;
        }
    }



    .flag {
        height: 25px;
        display: flex;
        align-items: center;
        gap: 10px;

        img {
            height: 100%;
        }
    }
}

.card:hover {


    .card-body {
        display: block !important;
        position: absolute;
        background: rgba(0, 8, 0, 0.775);
        width: 100%;
        height: 100%;
        color: white;
    }
}
</style>