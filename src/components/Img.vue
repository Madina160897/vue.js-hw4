<script>
export default {
    data() {
        return {
            images: [],
            src: "",
            isElement: true
        }
    },
    methods: {
        add() {
            if (this.src === '') {
                return
            }
            const newImg = {
                id: this.images.length + 1,
                src: this.src,
            }
            this.images.push(newImg)
            this.src = ''
        },
        deleteImg(id) {
            for (let i = 0; i < this.images.length; i++) {
                if (this.images[i].id == id) {
                    this.images.splice(i, 1)
                }
            }
        },
        getImg() {
            return Math.random(images);
        }
    }
}
</script>

<template>
    <div>
        <form class="Post" @submit.prevent>
            <input :value="src" @input="src = $event.target.value" type="text" placeholder="URL">
            <button class="btn" @click="add">Создать</button>
            <button class="btn" @click="getImg">Рандомная картинка</button>
            
        </form>

        <div class="fon">
            <div class="post-block" v-for="img in images">
                <img :src="img.src">
                <button class="btn" @click="deleteImg(img.id)">Удалить</button>
            </div>
        </div>

        <div class="fon">
            <div class="post-block" v-for="img in images" :key="img.id">
                <img :src="img.src">
            </div>
        </div>

    </div>
</template>

<style scoped>
.fon {
    width: 1890px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

.Post {
    display: flex;
    flex-direction: column;
    width: 400px;
    margin: 5% auto;
    border: 2px solid #2dcdd3;
    background-color: #f4f7f7;
    border-radius: 20px;
    padding: 5%;
    font-size: 16px;
}

input {
    margin-bottom: 20px;
    padding: 10px;
    font-size: 16px;
    border: 2px solid #5c9ea1;
    background-color: #ffffff9c;
    border-radius: 15px;
}

.btn {
    align-self: flex-end;
    font-size: 16px;
    padding: 10px;
    border-radius: 10px;
    background-color: rgb(216, 216, 216);
    border: 1px solid transparent;
    margin: 1%;
}

.post-block {
    display: flex;
    flex-direction: column;
    width: 400px;
    margin: 5% auto;
    border: 2px solid #2dcdd3;
    border-radius: 20px;
    padding: 5%;
}

img {
    width: 400px;
    height: 200px;
}
</style>