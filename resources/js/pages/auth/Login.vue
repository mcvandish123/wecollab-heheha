<script setup lang="ts">
import InputError from '@/components/InputError.vue';
import TextLink from '@/components/TextLink.vue';
import { Button } from '@/components/ui/button';
import { Checkbox } from '@/components/ui/checkbox';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import AuthBase from '@/layouts/AuthLayout.vue';
import { Form, Head, Link } from '@inertiajs/vue3';
import { LoaderCircle } from 'lucide-vue-next';
import { onMounted, onUnmounted } from 'vue';

defineProps<{
    status?: string;
    canResetPassword: boolean;
}>();

onMounted(() => {
  document.body.classList.add('auth-bg-override');
});
onUnmounted(() => {
  document.body.classList.remove('auth-bg-override');
});
</script>

<template>
    <div class="auth-bg">
        <AuthBase>
        <Head title="Log in" />
        <!-- Move logo above the h1/title -->
        <div class="flex justify-center mb-6">
            <img src="/imageSystem/logo.png" alt="Logo" class="h-20 w-20 object-contain" />
        </div>
        <div class="flex flex-col">
            <p class=" text-white font-semibold text-2xl text-center">Login to your Account</p>
            <p class="text-white text-center">Signup now</p>
        </div>
        <!-- The h1/title is rendered by AuthBase, so logo is now above it -->
        <div v-if="status" class="mb-4 text-sm font-medium text-center text-green-600">
            {{ status }}
        </div>
        <div class="mx-auto max-w-md w-full bg-white shadow-lg p-8 rounded-2xl text-black mb-100">
            <Form method="post" :action="route('login')" :reset-on-success="['password']" v-slot="{ errors, processing }" class="flex flex-col gap-6">
                <div class="grid gap-6">
                    <div class="grid gap-2">
                        <Label for="email">Email address</Label>
                        <Input
                            id="email"
                            type="email"
                            name="email"
                            autocomplete="email"
                            placeholder="email@example.com"
                        />
                        <InputError :message="errors.email" />
                    </div>
                    <div class="grid gap-2">
                        <div class="flex items-center justify-between">
                            <Label for="password">Password</Label>
                            <TextLink v-if="canResetPassword" :href="route('password.request')" class="text-sm text-red-500" :tabindex="5">
                                Forgot password?
                            </TextLink>
                        </div>
                        <Input
                            id="password"
                            type="password"
                            name="password"
                            required
                            :tabindex="2"
                            autocomplete="current-password"
                            placeholder="Password"
                        />
                        <InputError :message="errors.password" />
                    </div>
                    <div class="flex items-center justify-between">
                        <Label for="remember" class="flex items-center space-x-3">
                            <Checkbox id="remember" name="remember" :tabindex="3" />
                            <span>Remember me</span>
                        </Label>
                    </div>
                    <Button type="submit" class="w-full mt-2 bg-gray-600 text-white transition-none hover:bg-gray-600 hover:text-white cursor-pointer" 
                        :tabindex="4" 
                        :disabled="processing">
                        <LoaderCircle v-if="processing" class="w-4 h-4 animate-spin" />
                        Log in
                    </Button>
                </div>
                <div class="text-sm text-center text-black">
                    Don't have an account?
                    <TextLink :href="route('register')" class="text-red-500" :tabindex="5">Sign up</TextLink>
                </div>
            </Form>
        </div>
        </AuthBase>
    </div>
</template>

<style>
body {
  background: url('/imageSystem/login-bg.png') center/cover no-repeat !important;
  min-height: 100vh;
  width: 100vw;
  background-attachment: fixed;
}
</style>
<style scoped>
.auth-bg {
  min-height: 100vh;
  width: 100%;
}
</style>