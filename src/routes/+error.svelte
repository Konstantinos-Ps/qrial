<script lang="ts">
    //@ts-nocheck
    import { page } from "$app/stores";
    import { Button } from "bits-ui";
    import { ArrowLeft, Home } from "@lucide/svelte";

    function goBack() {
        history.back();
    }

    function goHome() {
        window.location.href = "/";
    }

    // Error messages mapping
    const errorMessages = {
        404: "The page you're looking for doesn't exist.",
        500: "Something went wrong on our end.",
        403: "You don't have permission to view this.",
        default: "An unexpected error occurred.",
    };

    $: errorMessage = errorMessages[$page.status] || errorMessages.default;
    $: pageTitle = `${$page.status} Error | Qrial`;
    $: pageDescription = `Error page: ${errorMessage}`;
</script>

<svelte:head>
    <title>{pageTitle}</title>
    <meta name="description" content={pageDescription} />
</svelte:head>

<div
    class="min-h-screen bg-gradient-to-br from-primary-100 to-secondary-100 dark:from-gray-900 dark:to-gray-800 flex flex-col items-center justify-center p-4 transition-colors"
>
    <div
        class="w-full max-w-md bg-white/80 dark:bg-gray-700/80 backdrop-blur-sm rounded-xl shadow-lg p-8 text-center space-y-6"
    >
        <!-- Error Code -->
        <div class="text-8xl font-bold text-gray-800 dark:text-white">
            {$page.status}
        </div>

        <!-- Error Message -->
        <h1 class="text-2xl font-semibold text-gray-800 dark:text-white">
            Oops!
        </h1>
        <p class="text-gray-600 dark:text-gray-300">
            {errorMessage}
        </p>

        <!-- Action Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <Button.Root
                onclick={goBack}
                class="flex items-center justify-center gap-2 px-4 py-2 bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 text-gray-800 dark:text-white rounded-lg transition-colors"
            >
                <ArrowLeft class="w-5 h-5" />
                Go Back
            </Button.Root>

            <Button.Root
                onclick={goHome}
                class="flex items-center justify-center gap-2 px-4 py-2 bg-primary-500 hover:bg-primary-600 text-white rounded-lg transition-colors"
            >
                <Home class="w-5 h-5" />
                Return Home
            </Button.Root>
        </div>
    </div>
</div>
