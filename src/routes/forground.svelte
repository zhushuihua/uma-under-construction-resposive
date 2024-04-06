<script lang="ts">
    import { onDestroy, onMount } from "svelte";

    const targetDate = new Date(2024, 4, 1);
    const now = new Date();
    let days: number;
    let hours: number;
    let minutes: string;
    let seconds: string;
    processTime();
    let interval: number;
    onMount(() => {
        interval = setInterval(processTime, 1000);
    });
    onDestroy(() => clearInterval(interval));
    function processTime() {
        const now = new Date();
        const diff = targetDate.getTime() - now.getTime();
        days = Math.floor(diff / (24 * 1000 * 60 * 60));
        let afterDays = diff % (24 * 1000 * 60 * 60);
        hours = Math.floor(afterDays / (1000 * 60 * 60));
        let afterHours = afterDays % (1000 * 60 * 60);
        minutes = Math.floor(afterHours / (1000 * 60))
            .toString()
            .padStart(2, "0");
        let afterMinutes = afterHours % (1000 * 60);
        seconds = Math.floor(afterMinutes / 1000)
            .toString()
            .padStart(2, "0");
        console.log("processing");
    }
</script>

<div
    class="z-10 relative w-screen top-0 h-screen min-h-[700px] text-white flex justify-center items-center p-8 text-center"
>
    <div class="space-y-16 max-w-3xl grow">
        <div class="flex items-center justify-between">
            <p class="text-5xl font-bold">UMA Maths</p>
            <div class="text-zinc-300 flex gap-4">
                <a href="https://apple.com"
                    ><svg
                        class="w-8 h-8"
                        aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg"
                        width="24"
                        height="24"
                        fill="currentColor"
                        viewBox="0 0 24 24"
                    >
                        <path
                            d="M17.537 12.625a4.421 4.421 0 0 0 2.684 4.047 10.96 10.96 0 0 1-1.384 2.845c-.834 1.218-1.7 2.432-3.062 2.457-1.34.025-1.77-.794-3.3-.794-1.531 0-2.01.769-3.275.82-1.316.049-2.317-1.318-3.158-2.532-1.72-2.484-3.032-7.017-1.27-10.077A4.9 4.9 0 0 1 8.91 6.884c1.292-.025 2.51.869 3.3.869.789 0 2.27-1.075 3.828-.917a4.67 4.67 0 0 1 3.66 1.984 4.524 4.524 0 0 0-2.16 3.805m-2.52-7.432A4.4 4.4 0 0 0 16.06 2a4.482 4.482 0 0 0-2.945 1.516 4.185 4.185 0 0 0-1.061 3.093 3.708 3.708 0 0 0 2.967-1.416Z"
                        />
                    </svg>
                </a>
                <a href="https://play.google.com">
                    <svg
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                        class="size-8"
                        viewBox="0 0 16 16"
                    >
                        <path
                            d="m10.213 1.471.691-1.26q.069-.124-.048-.192-.128-.057-.195.058l-.7 1.27A4.8 4.8 0 0 0 8.005.941q-1.032 0-1.956.404l-.7-1.27Q5.281-.037 5.154.02q-.117.069-.049.193l.691 1.259a4.25 4.25 0 0 0-1.673 1.476A3.7 3.7 0 0 0 3.5 5.02h9q0-1.125-.623-2.072a4.27 4.27 0 0 0-1.664-1.476ZM6.22 3.303a.37.37 0 0 1-.267.11.35.35 0 0 1-.263-.11.37.37 0 0 1-.107-.264.37.37 0 0 1 .107-.265.35.35 0 0 1 .263-.11q.155 0 .267.11a.36.36 0 0 1 .112.265.36.36 0 0 1-.112.264m4.101 0a.35.35 0 0 1-.262.11.37.37 0 0 1-.268-.11.36.36 0 0 1-.112-.264q0-.154.112-.265a.37.37 0 0 1 .268-.11q.155 0 .262.11a.37.37 0 0 1 .107.265q0 .153-.107.264M3.5 11.77q0 .441.311.75.311.306.76.307h.758l.01 2.182q0 .414.292.703a.96.96 0 0 0 .7.288.97.97 0 0 0 .71-.288.95.95 0 0 0 .292-.703v-2.182h1.343v2.182q0 .414.292.703a.97.97 0 0 0 .71.288.97.97 0 0 0 .71-.288.95.95 0 0 0 .292-.703v-2.182h.76q.436 0 .749-.308.31-.307.311-.75V5.365h-9zm10.495-6.587a.98.98 0 0 0-.702.278.9.9 0 0 0-.293.685v4.063q0 .406.293.69a.97.97 0 0 0 .702.284q.42 0 .712-.284a.92.92 0 0 0 .293-.69V6.146a.9.9 0 0 0-.293-.685 1 1 0 0 0-.712-.278m-12.702.283a1 1 0 0 1 .712-.283q.41 0 .702.283a.9.9 0 0 1 .293.68v4.063a.93.93 0 0 1-.288.69.97.97 0 0 1-.707.284 1 1 0 0 1-.712-.284.92.92 0 0 1-.293-.69V6.146q0-.396.293-.68"
                        />
                    </svg></a
                >
                <a href="#/">
                    <svg
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                        class="size-8"
                        viewBox="0 0 16 16"
                    >
                        <path
                            d="M0 8a8 8 0 1 1 16 0A8 8 0 0 1 0 8m7.5-6.923c-.67.204-1.335.82-1.887 1.855A8 8 0 0 0 5.145 4H7.5zM4.09 4a9.3 9.3 0 0 1 .64-1.539 7 7 0 0 1 .597-.933A7.03 7.03 0 0 0 2.255 4zm-.582 3.5c.03-.877.138-1.718.312-2.5H1.674a7 7 0 0 0-.656 2.5zM4.847 5a12.5 12.5 0 0 0-.338 2.5H7.5V5zM8.5 5v2.5h2.99a12.5 12.5 0 0 0-.337-2.5zM4.51 8.5a12.5 12.5 0 0 0 .337 2.5H7.5V8.5zm3.99 0V11h2.653c.187-.765.306-1.608.338-2.5zM5.145 12q.208.58.468 1.068c.552 1.035 1.218 1.65 1.887 1.855V12zm.182 2.472a7 7 0 0 1-.597-.933A9.3 9.3 0 0 1 4.09 12H2.255a7 7 0 0 0 3.072 2.472M3.82 11a13.7 13.7 0 0 1-.312-2.5h-2.49c.062.89.291 1.733.656 2.5zm6.853 3.472A7 7 0 0 0 13.745 12H11.91a9.3 9.3 0 0 1-.64 1.539 7 7 0 0 1-.597.933M8.5 12v2.923c.67-.204 1.335-.82 1.887-1.855q.26-.487.468-1.068zm3.68-1h2.146c.365-.767.594-1.61.656-2.5h-2.49a13.7 13.7 0 0 1-.312 2.5m2.802-3.5a7 7 0 0 0-.656-2.5H12.18c.174.782.282 1.623.312 2.5zM11.27 2.461c.247.464.462.98.64 1.539h1.835a7 7 0 0 0-3.072-2.472c.218.284.418.598.597.933M10.855 4a8 8 0 0 0-.468-1.068C9.835 1.897 9.17 1.282 8.5 1.077V4z"
                        />
                    </svg></a
                >
            </div>
        </div>
        <p class="px-8 text-3xl">We are under construction</p>
        <div class="flex justify-center gap-12 text-start font-mono">
            <div>
                <p class="text-6xl underline underline-offset-8 decoration-1">
                    {days}
                </p>
                <p class="text-sm mt-2">days</p>
            </div>
            <div>
                <p class="text-6xl underline underline-offset-8 decoration-1">
                    {hours}
                </p>
                <p class="text-sm mt-2">hours</p>
            </div>
            <div>
                <p class="text-6xl underline underline-offset-8 decoration-1">
                    {minutes}
                </p>
                <p class="text-sm mt-2">min</p>
            </div>
            <div>
                <p class="text-6xl underline underline-offset-8 decoration-1">
                    {seconds}
                </p>
                <p class="text-sm mt-2">sec</p>
            </div>
        </div>
        <div>
            <p class="text-xl mb-4">Stay In touch</p>
            <form class="flex gap-4 justify-center">
                <label for="">
                    <input
                        type="text"
                        value="Enter your email"
                        class="bg-zinc-600 p-2 rounded-l w-72 inline-block focus:ring-0 focus:outline-none focus:border-transparent"
                    />
                </label>
                <button class="bg-white text-zinc-950 px-8 py-2">submit</button>
            </form>
        </div>
    </div>
</div>
