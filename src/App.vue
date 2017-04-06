<template>
    <div id="app">
        <section class="section">
            <div class="container has-text-centered">

                <h2 class="subtitle is-3">Transitions and Animations</h2>

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

                <hr>

                <h2 class="title is-3">Dynamic Components</h2>

                <div class="block">
                    <button @click="switchComponent" class="button is-primary">Switch component</button>
                </div>

                <transition
                        enter-active-class="animated bounceInDown"
                        leave-active-class="animated bounceOutRight"
                        mode="out-in">
                    <component :is="selectedComponent"></component>
                </transition>

                <hr>

                <h2 class="title is-3">Group Transitions</h2>

                <div class="block">
                    <button @click="addRandomItem" class="button is-primary">Add Random Item</button>
                </div>

                <ul class="panel" style="height: 200px; overflow-y: auto">
                    <transition-group name="slide" appear>
                        <li v-for="(number, index) in numbers" :key="number" class="panel-block">
                            <span @click="removeItem(index)" class="panel-icon" style="cursor: pointer; ">
                                <span class="icon is-small">
                                    <i class="fa fa-close"></i>
                                </span>
                            </span>
                            {{ number }}

                        </li>
                    </transition-group>

                </ul>

            </div>
        </section>
    </div>
</template>

<script>
    import appSuccessMessage from './SuccessMessage.vue';
    import appDangerMessage from './DangerMessage.vue';

    export default {
        data() {
            return {
                showMessage: true,
                animations: ['fade', 'slide'],
                messageAnimation: 'fade',
                selectedComponent: 'app-success-message',
                numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9],
            };
        },
        components: {
            appSuccessMessage,
            appDangerMessage,
        },
        methods: {
            switchComponent() {
                if (this.selectedComponent == 'app-success-message') {
                    this.selectedComponent = 'app-danger-message';
                } else {
                    this.selectedComponent = 'app-success-message';
                }
            },
            removeItem(index) {
                this.numbers.splice(index, 1);
            },
            addRandomItem() {
                let position = Math.floor(Math.random() * this.numbers.length);
                this.numbers.splice(position, 0, this.numbers.length + 1);
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
        position: absolute;
    }

    .fade-leave-active {
        transition: opacity .6s ease-out;
        opacity: 0;
        position: absolute;
    }

    .fade-move {
        transition: transform .3s ease-out;
    }

    .slide-enter {

    }

    .slide-enter-active {
        animation: slide-in .3s ease-out forwards;
    }

    .slide-leave {
        position: absolute;
    }

    .slide-leave-active {
        animation: slide-out .3s ease-in forwards;
        position: absolute;
    }

    .slide-move {
        transition: transform .3s ease-out;
    }

    @keyframes slide-in {
        from {
            opacity: 0;
            transform: translateX(-100px);
        }
        to {
            opacity: 1;
            transform: translateX(0);
        }
    }

    @keyframes slide-out {
        from {
            opacity: 1;
            transform: translateX(0);
        }
        to {
            opacity: 0;
            transform: translateX(100px);
        }
    }

</style>
