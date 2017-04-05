<template>
    <div id="app">
        <section class="section">
            <div class="container has-text-centered">
                <h1 class="title is-2">Transitions and Animations</h1>
                <hr>
                <h2 class="subtitle is-3">Transitions</h2>
                <div class="block">
                    <button @click="showMessage = !showMessage" class="button is-primary">Fade Message</button>
                </div>
                <transition name="fade">
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
                showMessage: false
            }
        }
    }
</script>

<style>
    .fade-enter {
        opacity: 0;
    }

    .fade-enter-active {
        transition: opacity .3s ease-in;
    }

    .fade-leave {

    }

    .fade-leave-active {
        transition: opacity .3s ease-out;
        opacity: 0;
    }
</style>
