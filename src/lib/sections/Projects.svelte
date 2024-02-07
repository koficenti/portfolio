<script>
import Card from "$lib/component/Card.svelte";
import {scale} from "svelte/transition";
</script>

<div transition:scale class="px-14 flex flex-col gap-5 h-[40vh]">
    <div class="flex gap-5 slide-in-left flex-col md:flex-row">
        <Card>
            <div class="flex place-items-center flex-col gap-2">
                <h1 class="font-medium text-lg">NiceJobs</h1>
                <p>A job platform created with Angular</p>
                <a href="https://github.com/koficenti/nice-jobs" class="text-blue-400 underline">Github</a>
            </div>
        </Card>
        <Card>
            <div class="flex place-items-center flex-col gap-2">
                <h1 class="font-medium text-lg">Alpine-Demo</h1>
                <p>A typing speed test (rewritten) using alpinejs</p>
                <a href="https://github.com/koficenti/alpine-demo" class="text-blue-400 underline">Github</a>
            </div>
        </Card>
        <Card>
            <div class="flex place-items-center flex-col gap-2">
                <h1 class="font-medium text-lg">ExpressionParser</h1>
                <p>Calculator written in Rust using recursive descent</p>
                <a href="https://github.com/koficenti/ExpressionParser" class="text-blue-400 underline">Github</a>
            </div>
        </Card>
    </div>
    <div class="flex justify-end gap-5 slide-in-right  flex-col md:flex-row">
        <Card>
            <div class="flex place-items-center flex-col gap-2">
                <h1 class="font-medium text-lg">nice-ws</h1>
                <p>A reasonably nice websocket library</p>
                <a href="https://github.com/koficenti/nice-ws" class="text-blue-400 underline">Github</a>
            </div>
        </Card>
        <Card>
            <div class="flex place-items-center flex-col gap-2">
                <h1 class="font-medium text-lg">waffles_site</h1>
                <p>a crypto landing page written with NextJs</p>
                <a href="https://github.com/koficenti/waffles_site" class="text-blue-400 underline">Github</a>
            </div>
        </Card>
        <Card>
            <div class="flex place-items-center flex-col gap-2">
                <h1 class="font-medium text-lg">KofiBlog</h1>
                <p>A blog written with nextjs, using firebase.</p>
                <a href="https://github.com/koficenti/kofiblog" class="text-blue-400 underline">Github</a>
            </div>
        </Card>
    </div>
</div>

<style>
    @keyframes slideInRight {
        from {
            opacity: 0;
            transform: translateX(-100%);
        }
        to {
            opacity: 1;
            transform: translateX(0%);
        }
    }
    @keyframes slideInLeft {
        from {
            opacity: 0;
            transform: translateX(100%);
        }
        to {
            opacity: 1;
            transform: translateX(0%);
        }
    }
    .slide-in-right {
        opacity: 0;
        transform: translateX(100%);
        transform-origin: right;
        animation: slideInLeft 1s ease forwards;
        animation-delay: 0.5s;
    }
    .slide-in-left {
        opacity: 0;
        transform: translateX(-100%);
        transform-origin: left;
        animation: slideInRight 1s ease forwards;
        animation-delay: 0.5s;
    }
</style>