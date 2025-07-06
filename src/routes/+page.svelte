<script lang="ts">
    import { ToggleGroup } from "bits-ui";
    import { Button } from "bits-ui";
    import { Info } from "@lucide/svelte";

    import {
        MessageCircle, // WhatsApp
        Instagram,
        Linkedin,
        Twitter,
        Send, // Telegram
        Phone, // Signal
    } from "@lucide/svelte";
    let inputValue = "";
    let selectedNetwork:
        | "whatsapp"
        | "instagram"
        | "linkedin"
        | "twitter"
        | "telegram"
        | "signal" = "whatsapp";
    function generateSocialQR(value: string, network: string): string {
        const cleanValue =
            network === "whatsapp"
                ? value.replace(/\D/g, "")
                : value.replace(/[^\w@]/g, "");

        const socialUrl = {
            whatsapp: `https://wa.me/${cleanValue}`,
            instagram: `https://instagram.com/${cleanValue}`,
            linkedin: `https://linkedin.com/in/${cleanValue}`,
            twitter: `https://twitter.com/${cleanValue}`,
            telegram: `https://t.me/${cleanValue}`,
            signal: `https://signal.me/${cleanValue}`,
        }[network];

        return `https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=${encodeURIComponent(socialUrl)}`;
    }

    $: qrCodeUrl = inputValue
        ? generateSocialQR(inputValue, selectedNetwork)
        : "";

    $: placeholder = {
        whatsapp: "Enter phone number (e.g., 1234567890)",
        instagram: "Enter Instagram handle (e.g., username)",
        linkedin: "Enter LinkedIn username",
        twitter: "Enter X/Twitter handle (without @)",
        telegram: "Enter Telegram username",
        signal: "Enter Signal username",
    }[selectedNetwork];

    const pageTitle = "QRials - Generate QR Codes for Social Media";
    const pageDescription =
        "Generate QR codes for WhatsApp, Instagram, LinkedIn, Twitter, Telegram, and Signal.";
    const pageKeywords =
        "QR code generator, social media QR codes, WhatsApp QR code, Instagram QR code, LinkedIn QR code, Twitter QR code, Telegram QR code, Signal QR code";
    const pageAuthor = "QRials Team";
</script>

<svelte:head>
    <title>{pageTitle}</title>
    <meta name="description" content={pageDescription} />
    <meta name="keywords" content={pageKeywords} />
    <meta name="author" content={pageAuthor} />
</svelte:head>
<div
    class="min-h-screen bg-gradient-to-br from-primary-100 to-secondary-100 dark:from-gray-900 dark:to-gray-800 flex flex-col items-center justify-center p-4 transition-colors"
>
    <div
        class="w-full max-w-3xl bg-white/80 dark:bg-gray-700/80 backdrop-blur-sm rounded-xl shadow-lg p-6 space-y-6 transition-all"
    >
        <!-- Title -->
        <div class="text-center space-y-2">
            <h1 class="text-3xl font-bold text-gray-800 dark:text-white">
                QR Code Generator
            </h1>
            <p class="text-gray-600 dark:text-gray-300">
                Generate QR codes for your social media profiles.
            </p>
        </div>

        <!-- Network Selector -->
        <ToggleGroup.Root
            type="single"
            bind:value={selectedNetwork}
            class="grid grid-cols-2 md:grid-cols-3 gap-3"
        >
            <ToggleGroup.Item
                value="whatsapp"
                class="flex items-center justify-center gap-2 p-3 rounded-lg transition-all bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 data-[state=on]:bg-green-500 data-[state=on]:text-white"
            >
                <MessageCircle class="w-5 h-5" />
                WhatsApp
            </ToggleGroup.Item>
            <ToggleGroup.Item
                value="instagram"
                class="flex items-center justify-center gap-2 p-3 rounded-lg transition-all bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 data-[state=on]:bg-pink-500 data-[state=on]:text-white"
            >
                <Instagram class="w-5 h-5" />
                Instagram
            </ToggleGroup.Item>
            <ToggleGroup.Item
                value="linkedin"
                class="flex items-center justify-center gap-2 p-3 rounded-lg transition-all bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 data-[state=on]:bg-blue-600 data-[state=on]:text-white"
            >
                <Linkedin class="w-5 h-5" />
                LinkedIn
            </ToggleGroup.Item>
            <ToggleGroup.Item
                value="twitter"
                class="flex items-center justify-center gap-2 p-3 rounded-lg transition-all bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 data-[state=on]:bg-blue-400 data-[state=on]:text-white"
            >
                <Twitter class="w-5 h-5" />
                Twitter
            </ToggleGroup.Item>
            <ToggleGroup.Item
                value="telegram"
                class="flex items-center justify-center gap-2 p-3 rounded-lg transition-all bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 data-[state=on]:bg-blue-500 data-[state=on]:text-white"
            >
                <Send class="w-5 h-5" />
                Telegram
            </ToggleGroup.Item>
            <ToggleGroup.Item
                value="signal"
                class="flex items-center justify-center gap-2 p-3 rounded-lg transition-all bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 data-[state=on]:bg-purple-500 data-[state=on]:text-white"
            >
                <Phone class="w-5 h-5" />
                Signal
            </ToggleGroup.Item>
        </ToggleGroup.Root>

        <!-- Input Field -->
        <div class="space-y-2">
            <label
                for="social-input"
                class="block text-sm font-medium text-gray-700 dark:text-gray-300"
            >
                {placeholder}
            </label>
            <input
                id="social-input"
                bind:value={inputValue}
                class="w-full p-3 border border-gray-300 dark:border-gray-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent dark:bg-gray-700 dark:text-white shadow-sm focus:shadow-md transition-all"
                {placeholder}
            />
        </div>

        <!-- QR Code Display -->
        {#if qrCodeUrl}
            <div
                class="flex flex-col items-center space-y-4 p-6 bg-white dark:bg-gray-800 rounded-lg shadow-md group hover:scale-[1.02] transition-transform"
            >
                <img
                    src={qrCodeUrl}
                    alt="QR Code"
                    class="w-48 h-48 border-2 border-gray-200 dark:border-gray-600 rounded-lg"
                />
                <p class="text-sm text-gray-500 dark:text-gray-400">
                    Scan to open {selectedNetwork} profile
                </p>
                <Button.Root
                    href={qrCodeUrl}
                    class="mt-2 px-4 py-2 bg-primary-500 hover:bg-primary-600 text-white rounded-lg transition-colors"
                >
                    Download QR Code
                </Button.Root>
            </div>
        {/if}
    </div>
    <!--About -->
    <div class="flex justify-center">
        <Button.Root
            href="/about"
            class="flex items-center justify-center gap-2 px-4 py-2 bg-gray-100 hover:bg-gray-200 dark:bg-gray-600 dark:hover:bg-gray-500 text-gray-800 dark:text-white rounded-lg transition-colors"
        >
            <Info class="w-5 h-5" />
            About QRials
        </Button.Root>
    </div>
</div>
