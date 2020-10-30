<template>
    <div class="input">
        <input 
            type="text"
            :value="value"
            @keypress.prevent="enterValue"
        >
        <ul>
            <li 
                v-for="(error,index) in errors"
                :key="index"
            >
                {{error}}
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "StringInput",

    data() {
        return {
            errors: []
        }
    },
    
    props : {
        value: {
            type: [String, Number],
            required: true
        },
        isNumber: {
            type: Boolean,
            default: false
        },
        isEmail: {
            type: Boolean,
            default: false
        },
        required: {
            type: Boolean,
            default: false
        },
        minLength: {
            type: Number,
            default: null
        },
        maxLength: {
            type: Number,
            default: null
        }
    },

    methods: {
        enterValue(e) {
            this.errors = []
            let status = true

            if(this.isNumber && !this.handleIsNumber(e)) {
                status = false
            }
            
            if(status) {
                this.$emit("input", this.value + e.key)
            }

        },

        handleIsNumber(e) {
            const numbers = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
            const status = numbers.findIndex(n => n === e.key) > -1
            if(!status) {
                this.errors.push("sadece rakam girilebilir")
            } 
            return status
        }
    }
}

</script>

<style scoped>

</style>