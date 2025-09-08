<template>
    <AuthBase>
        <Head title="Register" />

        <!-- Logo above the title, same as Login.vue -->
        <div class="flex justify-center mb-6">
            <img src="/imageSystem/logo.png" alt="Logo" class="h-20 w-20 object-contain" />
        </div>
        <div class="flex flex-col">
            <p class="text-white font-semibold text-2xl text-center">Create an Account</p>
            <p class="text-white text-center">Sign up</p>
        </div>

        <div class="mx-auto max-w-md w-full bg-white shadow-lg p-8 rounded-2xl text-black mb-100">
            <Form
                method="post"
                :action="route('register')"
                :reset-on-success="['password', 'password_confirmation']"
                v-slot="{ errors, processing }"
                class="flex flex-col gap-6"
            >
                <div class="grid gap-6">
                    <div class="grid gap-2">
                        <Label for="name">Name</Label>
                        <Input id="name" type="text" required autofocus :tabindex="1" autocomplete="name" name="name" placeholder="Full name" class="placeholder:text-black" />
                        <InputError :message="errors.name" />
                    </div>

                    <div class="grid gap-6">
                        <Label for="email">Email address</Label>
                        <Input id="email" type="email" required :tabindex="2" autocomplete="email" name="email" placeholder="email@example.com" class="placeholder:text-black" />
                        <InputError :message="errors.email" />
                    </div>

                    <div class="grid gap-2">
                        <Label for="password">Password</Label>
                        <Input id="password" type="password" required :tabindex="3" autocomplete="new-password" name="password" placeholder="Password" class="placeholder:text-black" />
                        <InputError :message="errors.password" />
                    </div>

                    <div class="grid gap-2">
                        <Label for="password_confirmation">Confirm password</Label>
                        <Input
                            id="password_confirmation"
                            type="password"
                            required
                            :tabindex="4"
                            autocomplete="new-password"
                            name="password_confirmation"
                            placeholder="Confirm password"
                            class="placeholder:text-black"
                        />
                        <InputError :message="errors.password_confirmation" />
                    </div>

                    <div class="bg-gray-200 rounded-lg p-4 flex justify-center">
                        <Button
                            type="submit"
                            class="w-full mt-2 bg-gray-600 text-white transition-none hover:bg-gray-600 hover:text-white cursor-pointer"
                            tabindex="5"
                            :disabled="processing"
                        >
                            <LoaderCircle v-if="processing" class="w-4 h-4 animate-spin" />
                            Create account
                        </Button>
                    </div>
                </div>

                <div class="text-sm text-center text-black">
                    Already have an account?
                    <TextLink :href="route('login')" class="text-red-500" :tabindex="6">Log in</TextLink>
                </div>
            </Form>
        </div>
    </AuthBase>
</template>

<script setup lang="ts">
import InputError from '@/components/InputError.vue';
import TextLink from '@/components/TextLink.vue';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import AuthBase from '@/layouts/AuthLayout.vue';
import { Form, Head } from '@inertiajs/vue3';
import { LoaderCircle } from 'lucide-vue-next';
</script>

<style scoped>
body, html {
    background: #111 !important;
}
</style>
