<script lang="ts">
    import stchr_logo from "$lib/assets/STCHr_thumbnail_.png";
    import { browser } from "$app/environment";

    function navigateToProduct() {
        if (browser) {
            window.location.href =
                "https://www.drivethrurpg.com/en/product/520092/stchr-pocketquest-2025";
        }
    }
</script>

<div class="flex flex-row items-center justify-center gap-12 padding-12">
    <img
        src={stchr_logo}
        alt="STCHr Logo"
        class="w-128 h-auto rounded-lg shadow-md hover:shadow-lg transition-shadow duration-300"
    />

    <div class="flex flex-col items-center justify-center h-screen">
        <h1 class="text-4xl font-bold mb-8">SLEEP WELL, STCHr</h1>
        <p class="text-2xl mb-4">
            A desperate future has lead humanity to pursue any avenue in order
            to scrape by. Sleep was once a bastion thought untouchable. Now, it
            is an opportunity where the only skill required is dreaming.
        </p>
        <p class="text-lg mb-6">
            Wearing modified headsets, STCHrs prowl through the vivid
            dreamscapes housed in Weaves. Weaves contain mysterious, unprocessed
            data that through the art of STCHing can be sorted, solved, and sent
            back to the up-loader in exchange for trace-less funds.
        </p>
        <p class="text-md mb-4">
            The act of STCHing is outlawed. STCHrs therefore work anonymously,
            concealed behind online personas. You, and possibly some randos you
            met online, have a shot to escape outside the system that has beat
            you down. Don’t let your dream slip away.
        </p>
        <p class="text-lg mb-6">
            Sleep when you’re dead STCHr. You’ve got work to do.
        </p>
        <a
            href="https://www.drivethrurpg.com/en/product/520092/stchr-pocketquest-2025"
            class="btn btn-info btn-lg">Buy Now!</a
        >
    </div>
</div>
