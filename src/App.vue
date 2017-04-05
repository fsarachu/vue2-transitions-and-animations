<template>
    <div id="app">
        <section class="section">
            <div class="container has-text-centered">
                <h1 class="title is-2">Transitions and Animations</h1>
                <hr>
                <h2 class="subtitle is-3">Transitions</h2>
                <div class="block">
                    <button @click="showMessage = !showMessage" class="button is-primary">Toggle Message</button>
                </div>
                <article v-if="showMessage" class="message is-primary">
                    <div class="message-header">
                        <p>Some Message</p>
                    </div>
                    <div class="message-body">
                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Sapiente, sit.
                    </div>
                </article>
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

</style>
