<template>
    <div id="vueapp" class="vue-app">
        <div class="row example-wrapper">
            <div class="col-xs-12 col-sm-6 offset-sm-3 example-col">
                <div class="card">
                    <div class="card-block">
                        <form class="k-form" @submit="handleSubmit">
                            <fieldset>
                                <legend>Create new account:</legend>
                                <div class="mb-3">
                                    <k-input
                                            :name="'username'"
                                            :style='{ width: "100%" }'
                                            :label="'First Name'"
                                            :pattern="'[A-Za-z]+'"
                                            :min-length="2"
                                            :required="true"
                                    >
                                    </k-input>
                                </div>
                                <div class="mb-3">
                                    <k-input
                                            :name="'password'"
                                            type="password"
                                            :style="{ width: '100%' }"
                                            :label="'Password'"
                                            :required="true"
                                            :min-length="6"
                                            :max-length="18"
                                    />
                                </div>
                                <div class="mb-3">
                                    <k-input
                                            :name="'confirmPassword'"
                                            :type="'password'"
                                            :style="{ width: '100%' }"
                                            :label="'Confirm Password'"
                                            :min-length="6"
                                            :max-length="18"
                                    />
                                </div>
                                <div class="mb-3">
                                    <k-input
                                            :name="'email'"
                                            :type="'email'"
                                            :style="{ width: '100%' }"
                                            :label="'Email address'"
                                            :required='true'
                                    />
                                </div>
                            </fieldset>
                            <input type="submit" class="k-button k-primary" value="Search" />
                        </form>
                    </div>
                </div>
            </div>
            <div v-if="success"
                 class="alert alert-success"
                 :style="{ position: 'absolute' }"
            >
                Form submitted!
            </div>
        </div>
    </div>
</template>

<script>
import { Input } from '@progress/kendo-vue-inputs';
export default {
    name: "custForm",
    data: function(){
        return {
            success: false
        }
    },
    methods: {
        handleSubmit (event) {
            event.preventDefault();
            this.success = true;
            setTimeout(() => { this.success = false; }, 3000);
        }
    }
}
</script>

<style scoped>

</style>
