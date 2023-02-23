<script>
import { RouterLink } from 'vue-router';

export default {
        name: 'HomeView',
        components: {
                RouterLink,
        },
        data() {
                return {
                        faces: [
                                { to: '/', text: 'Home', image: '@/assets/logo.svg' },
                                { to: '/', text: '', image: '@/assets/logo.svg' },
                                { to: '/gallery', text: 'Gallery', image: '@/assets/logo.svg' },
                                { to: '/about', text: 'About', image: '@/assets/logo.svg' },
                                { to: '/', text: '', image: '@/assets/logo.svg' },
                                { to: '/contact', text: 'Contact', image: '@/assets/logo.svg' },
                        ],
                        cubeTransform: '',
                };
        },
        mounted() {
                document.addEventListener('mousemove', (event) => {
                        const angleX = (event.clientX / window.innerWidth) * 360;
                        const angleY = (event.clientY / window.innerHeight) * 360;
                        this.cubeTransform = `rotateX(${angleY}deg) rotateY(${angleX}deg)`;
                });
        },
        methods: {
                faceClass(index) {
                        return `face-${index}`;
                },
        },
};
</script>
<template>
        <div class="container">
                <div class="row banner align-items-center">
                        <div id="cube-container" class="d-flex justify-content-center align-items-center">
                                <div class="cube" v-bind:style="{ transform: cubeTransform }">

                                        <router-link v-for="(face, index) in faces" :to="face.to" :class="faceClass(index)"
                                                :key="index">
                                                <div class="text-box">
                                                        <span class="face-text text-head">{{ face.text }}</span>
                                                </div>
                                        </router-link>
                                </div>
                        </div>
                </div>
        </div>
</template>

<style scoped>
#cube-container {
        overflow: hidden;
        height: 400px;
}

.cube {
        position: relative;
        width: 200px;
        height: 200px;
        transform-style: preserve-3d;
}

.cube a {
        position: absolute;
        width: 200px;
        height: 200px;
        display: block;
        border: 3px solid #1C2331;
}

.face-text {
        display: flex;
        align-items: center !important;
        justify-content: center;
        font-size: 24px;
        font-weight: bold;
        color: rgb(255, 255, 255);
        text-align: center;
        rotate: 180deg;
        padding-bottom: 76px;
}

.face-0 {
        transform: translateZ(100px);
        background-image: url(./img/headerPad.jpg);
}

.face-1 {
        transform: rotateY(180deg) translateZ(100px);
        background-image: url(./img/headerPad.jpg);
}

.face-2 {
        transform: rotateY(90deg) translateZ(100px);
        background-image: url(./img/headerPad.jpg);
}

.face-3 {
        transform: rotateY(-90deg) translateZ(100px);
        background-image: url(./img/headerPad.jpg);
}

.face-4 {
        transform: rotateX(90deg) translateZ(100px);
        background-image: url(./img/headerPad.jpg);
}

.face-5 {
        transform: rotateX(-90deg) translateZ(100px);
        background-image: url(./img/headerPad.jpg);
}

.face-0:hover,
.face-1:hover,
.face-2:hover,
.face-3:hover,
.face-4:hover,
.face-5:hover {
        background-color: rgb(171, 0, 250);
}

.cube a:hover {
        opacity: 0.8;
}

.cube a:active {
        opacity: 1;
}
</style>




