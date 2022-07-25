<template>
    <div class="modal">

        <div class="modal-mask">
            <div class="modal-wrapper">
                <div class="modal-container" :class="{ mod: isActive3 }">

                    <div class="modal-header">

                        <slot name="header">
                            <h3>{{ text1 }}</h3>
                        </slot>
                    </div>

                    <div class="modal-body">
                        <slot name="body">
                            {{ text3 }}
                        </slot>
                    </div>

                    <div class="modal-footer">
                        <slot name="footer">
                            приходит из родительского компанента
                        </slot>
                        <button class="modal-close-button" @click="$emit('close')">
                            Закрыть окно
                        </button>

                        <button class="modal-close-button" v-on:click="isActive3 = !isActive3">
                            Увеличить окно в 1,5 раза
                        </button>

                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<script>
export default {
    name: 'ModalWindow',
    props: {
        msg: String
    },
    data() {
        return {
            text1: 'Показать модальное окно',
            text3: 'Текст модального окна',
            isActive3: false
        }
    }
}
</script>

<style>
.modal-mask {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: table;
}

.modal-wrapper {
    display: table-cell;
    vertical-align: middle;
}

.modal-container {
    width: 400px;
    height: 200px;
    margin: 0px auto;
    padding: 20px 30px;
    background-color: #fff;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    font-family: Helvetica, Arial, sans-serif;
}

.modal-container.mod {
    width: 600px;
    height: 300px;

}

.modal-header h3 {
    margin-top: 0;
    color: #42b983;
}

.modal-body {
    margin: 20px 0;
}

.modal-footer h3 {
    margin-top: 0;
    color: red;
}

.modal-close-button {
    display: block;
    margin-top: 1rem;

}
</style>
