<template>
    <div class="header">
        <h3>Quotes Added</h3>
        <div class="progress header__progress">
            <div class="progress-bar" role="progressbar" :aria-valuenow="quotesCount * 10"
                 aria-valuemin="0" aria-valuemax="100" :style="{ width: quotesCount * 10 + '%'}">
                {{ quotesCount }} / 10
            </div>
        </div>
    </div>

</template>

<script>
    import { eventBus } from '../main.js';

    export default {
        name: "Header",
        data: function(){
            return {
                quotesCount: 0,
            }
        },
        created() {
            eventBus.$on('quotesArrayLength', (quotesCount) => {
                this.quotesCount = quotesCount;
            });
        }
    }
</script>

<style scoped>

</style>