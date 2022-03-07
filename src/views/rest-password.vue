
<template>
    <main>
        <!-- component -->
        <div>
            <div class="relative min-h-screen grid bg-black">
                <div
                    class="flex flex-col sm:flex-row items-center md:items-start sm:justify-center md:justify-start flex-auto min-w-0"
                >
                    <div
                        class="relative sm:w-1/2 xl:w-3/5 bg-blue-500 h-full hidden md:flex flex-auto items-center justify-center p-10 overflow-hidden text-white bg-no-repeat bg-cover relative"
                        style="
              background-image: url(https://i.postimg.cc/mrgPMqpP/logo.png);
            "
                    >
                        <div class="absolute bg-black opacity-25 inset-0 z-0"></div>
                        <div class="w-full lg:max-w-2xl md:max-w-md z-10 items-center text-center">
                            <div
                                class="font-bold leading-tight mb-6 mx-auto w-full content-center items-center"
                            ></div>
                        </div>
                    </div>

                    <div
                        class="md:flex md:items-center md:justify-left w-full sm:w-auto md:h-full xl:w-1/2 p-8 md:p-10 lg:p-14 sm:rounded-lg md:rounded-none"
                    >
                        <div class="max-w-xl w-full space-y-12">
                            <div class="lg:text-left text-center">
                                <div class="flex items-center justify-center">
                                    <div
                                        class="bg-black flex flex-col w-80 border border-gray-900 rounded-lg px-8 py-10"
                                    >
                                    <h1 class=" text-white">rest your password</h1>
                                        <form
                                            class="flex flex-col space-y-12 mt-8"
                                            @submit.prevent="submit"
                                        >
                                            <input
                                                type="text"
                                                v-model="password"
                                                placeholder="new password :"
                                                class="border rounded-lg py-3 px-3 bg-black border-indigo-600 placeholder-white-500 text-white"
                                            />

                                          

                                            <button
                                                class="border border-indigo-600 bg-sky-600 hover:bg-white hover:text-black text-white rounded-lg py-3 font-semibold"
                                                routerLink="/dashboard"
                                            >update password</button>

                                            <p v-if="error" class="bg-white">{{ error }}</p>
                                        </form>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>
<script setup>
import { ref } from 'vue';
import axios from 'axios'
import { useRouter } from 'vue-router';
const error = ref()
const router = useRouter()
const password = ref()

// const {token,id}=data

const submit = async () => {
    console.log('5555');
    try {
        const data = await axios.post(`http://localhost:2020/rest-password?token=${token}&id=${data._id}`, {
            password:password.value
            
    
        })
        console.log(data,"sss");
        router.push('/log')


    } catch (e) {
        error.value = e.response



    }

}

</script>