<div class="flex place-items-end justify-center h-[40vh] opened">
    <div class="bg-red-400 shadow rounded-md w-9/12 h-full mb-5 flex justify-center place-items-center">
    </div>
</div>

<style>
    @keyframes Opened {
        from {
            transform: translateY(100%);
        }
        to {
            transform: translateY(0%);
        }
    }
    .opened {
        transform: translateY(100%);
        transform-origin: bottom;
        animation: Opened 0.5s ease forwards;
    }
</style>