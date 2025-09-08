<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { type BreadcrumbItem } from '@/types';
import { Head } from '@inertiajs/vue3';

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Dashboard',
        href: '/dashboard',
    },
];
</script>

<template>
    <Head title="Dashboard" />

    <AppLayout :breadcrumbs="breadcrumbs">
        <div class="flex h-full flex-1 flex-col gap-4 rounded-xl p-4 overflow-x-auto">
            <div class="grid auto-rows-min gap-4 md:grid-cols-3">
                <div class="relative aspect-video overflow-hidden rounded-xl border border-sidebar-border/70 dark:border-sidebar-border">
                    <!-- Content for box 1 -->
                </div>
                <div class="relative aspect-video overflow-hidden rounded-xl border border-sidebar-border/70 dark:border-sidebar-border">
                    <!-- Content for box 2 -->
                </div>
                <div class="relative aspect-video overflow-hidden rounded-xl border border-sidebar-border/70 dark:border-sidebar-border">
                    <!-- Content for box 3 -->
                </div>
            </div>
            <div class="relative min-h-100vh flex-1 rounded-xl border border-sidebar-border/70 md:min-h-min dark:border-sidebar-border">
                <!-- Removed <PlaceholderPattern /> to remove slanted lines -->
            </div>
        </div>
    </AppLayout>
</template>

<style scoped>
/* Main dashboard area */
.flex {
    background-color: #FFFAE9;
    color: #4b824b;
}

/* Accent for cards and borders */
.border-sidebar-border {
    border-color: #4b824b !important;
}

/* Card backgrounds */
.grid > div {
    background-color: #4b824b;
    color: #FFFAE9;
    border-color: #4b824b !important;
}

/* Main content area */
.rounded-xl,
.min-h-100vh {
    background-color: #FFFAE9;
    color: #4b824b;
    border-color: #4b824b !important;
}

/* Placeholder accent */
.placeholder-accent {
    background-color: #4b824b;
    color: #FFFAE9;
}

/* Sidebar styles (add these to your sidebar component or global CSS) */
.sidebar,
.sidebar-content {
    background-color: #FFFAE9 !important;
    color: #4b824b !important;
}

/* Sidebar links */
.sidebar a,
.sidebar-content a {    
    color: #4b824b !important;
}

/* Sidebar active item */
.sidebar .active,
.sidebar-content .active {
    background-color: #4b824b !important;
    color: #FFFAE9 !important;
}

/* Make the big rectangle at the bottom use #4b824b as background and #FFFAE9 as text */
.min-h-100vh {
    background-color: #4b824b !important;
    color: #FFFAE9 !important;
    border-color: #4b824b !important;
}
</style>
