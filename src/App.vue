<template>
    <div id="app">
        <section class="section">
            <div class="container has-text-centered">

                <h1 class="title is-2">Transitions and Animations</h1>

                <hr>

                <h2 class="subtitle is-3">Transitions</h2>

                <div class="block">
                    <span class="select">
                        <select v-model="messageAnimation">
                            <option v-for="animation in animations" :value="animation">{{ animation }}</option>
                        </select>
                    </span>
                    <button @click="showMessage = !showMessage" class="button is-primary">Toggle Message</button>
                </div>

                <transition :name="messageAnimation" appear>
                    <article v-if="showMessage" class="message is-primary">
                        <div class="message-header">
                            <h3>Some Message</h3>
                        </div>
                        <p class="message-body">
                            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Sapiente, sit.
                        </p>
                    </article>
                </transition>

            </div>
        </section>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                showMessage: true,
                messageAnimation: 'fade',
                animations: ['fade', 'slide']
            }
        }
    }
</script>

<style>
    .fade-enter {
        opacity: 0;
    }

    .fade-enter-active {
        transition: opacity .6s ease-in;
    }

    .fade-leave {

    }

    .fade-leave-active {
        transition: opacity .6s ease-out;
        opacity: 0;
    }

    .slide-enter {

    }

    .slide-enter-active {
        animation: slide-in .6s ease-out forwards;
    }

    .slide-leave {

    }

    .slide-leave-active {
        animation: slide-out .6s ease-in forwards;
    }

    @keyframes slide-in {
        from {
            opacity: 0;
            transform: translateY(50px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    @keyframes slide-out {
        from {
            opacity: 1;
            transform: translateY(0);
        }
        to {
            opacity: 0;
            transform: translateY(100px);
        }
    }

</style>
