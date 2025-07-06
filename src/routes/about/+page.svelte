<script lang="ts">
    import { Button } from "bits-ui";
    import { ArrowRight, Zap, Code, Heart } from "@lucide/svelte";

    const pageTitle = "About Qrial | QR Code Generator";
    const pageDescription =
        "Learn about Qrial - the simple, powerful QR code generator for social media profiles";
    const pageKeywords =
        "QR code generator, QR code, QR code creator, QR code maker, QR code generator for social media";
    const pageAuthor = "Qrial Team";
</script>

<svelte:head>
    <title>{pageTitle}</title>
    <meta name="description" content={pageDescription} />
    <meta name="keywords" content={pageKeywords} />
    <meta name="author" content={pageAuthor} />
</svelte:head>

<div
    class="min-h-screen bg-gradient-to-br from-primary-100 to-secondary-100 dark:from-gray-900 dark:to-gray-800 py-12 px-4 sm:px-6 lg:px-8"
>
    <div class="max-w-4xl mx-auto">
        <!-- Hero Section -->
        <div class="text-center mb-16">
            <h1 class="text-4xl font-bold text-gray-800 dark:text-white mb-4">
                About Qrial
            </h1>
            <p
                class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto"
            >
                Making QR codes simple and accessible for everyone
            </p>
        </div>

        <!-- Features Grid -->
        <div class="grid md:grid-cols-3 gap-8 mb-16">
            <div
                class="bg-white/80 dark:bg-gray-700/80 backdrop-blur-sm p-6 rounded-xl shadow-md"
            >
                <Zap class="w-10 h-10 text-white mb-4 mx-auto" />
                <h3
                    class="text-lg font-semibold text-gray-800 dark:text-white mb-2 text-center"
                >
                    Instant Generation
                </h3>
                <p class="text-gray-600 dark:text-gray-300 text-center">
                    Create QR codes for any social profile in seconds
                </p>
            </div>

            <div
                class="bg-white/80 dark:bg-gray-700/80 backdrop-blur-sm p-6 rounded-xl shadow-md"
            >
                <Code class="w-10 h-10 text-white mb-4 mx-auto" />
                <h3
                    class="text-lg font-semibold text-gray-800 dark:text-white mb-2 text-center"
                >
                    Developer Friendly
                </h3>
                <p class="text-gray-600 dark:text-gray-300 text-center">
                    Built with modern web technologies for reliability
                </p>
            </div>

            <div
                class="bg-white/80 dark:bg-gray-700/80 backdrop-blur-sm p-6 rounded-xl shadow-md"
            >
                <Heart class="w-10 h-10 text-white mb-4 mx-auto" />
                <h3
                    class="text-lg font-semibold text-gray-800 dark:text-white mb-2 text-center"
                >
                    Free Forever
                </h3>
                <p class="text-gray-600 dark:text-gray-300 text-center">
                    No paywalls, no tracking, just useful tools
                </p>
            </div>
        </div>

        <!-- Mission Statement -->
        <div
            class="bg-white/80 dark:bg-gray-700/80 backdrop-blur-sm rounded-xl shadow-md p-8 mb-16"
        >
            <h2 class="text-2xl font-bold text-gray-800 dark:text-white mb-4">
                Our Mission
            </h2>
            <p class="text-gray-600 dark:text-gray-300 mb-6">
                At Qrial, we believe connecting your offline and online presence
                should be effortless. Our QR code generator removes the
                technical barriers, letting you focus on what matters - growing
                your network and sharing your content.
            </p>
            <p class="text-gray-600 dark:text-gray-300">
                Whether you're a business owner, creator, or just someone who
                wants to share contacts easily, we've built this tool to work
                seamlessly for everyone.
            </p>
        </div>

        <!-- CTA Section -->
        <div class="text-center">
            <h2 class="text-2xl font-bold text-gray-800 dark:text-white mb-6">
                Ready to create your QR code?
            </h2>
            <Button.Root
                href="/"
                class="inline-flex items-center gap-2 px-6 py-3 bg-primary-500 hover:bg-primary-600 text-white rounded-lg transition-colors text-lg"
            >
                Generate Now
                <ArrowRight class="w-5 h-5" />
            </Button.Root>
        </div>
    </div>
</div>
