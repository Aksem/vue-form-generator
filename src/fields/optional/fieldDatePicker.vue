<template>
<datepicker :placeholder="schema.placeholder" name="schema.inputName" readonly="schema.readonly" id="getFieldID(schema)" :format="getDateFormat()" v-model="value"></datepicker>
</template>

<script>
    /* global $ */
    import abstractField from "../abstractField";
    import Datepicker from 'vuejs-datepicker';


    let format = "yyyy-MM-dd";

    export default {
        mixins: [ abstractField ],
        components: {
            datepicker: Datepicker
        },

        methods: {
            getDateFormat: function () {
                if (this.schema.datePickerOptions && this.schema.datePickerOptions.format) {
                    return this.schema.datePickerOptions.format;
                } else {
                    return format;
                }
            }
        },
        beforeDestroy() {
            if (window.$ && window.$.fn.datetimepicker){
                $(this.$el).data("DatePicker").destroy();
            }
        }
    };
</script>

<style>
</style>
