<script setup>
    import MainLayout from '@/Layouts/MainLayout.vue';
    import TextInput from '@/Components/TextInput.vue';
    import InputLabel from '@/Components/InputLabel.vue';
    import { Link } from '@inertiajs/vue3';

    function formatMoney(value){
        return new Intl.NumberFormat("id-ID").format(value)
    }

    import mobil from '../mobil';
    let totalUang = parseInt(mobil.harga) + (parseInt(mobil.harga) * (parseInt(mobil.dp) / 100)) + (parseInt(mobil.harga) * (mobil.inflasi / 100));
    let jumlahUang = mobil.uang;
    let targetInvestasi = mobil.target;
    let returnInvestasi = mobil.instrumen;
    let jumlahPeriode = mobil.waktu;
    let hasilInvestasi = (parseInt(mobil.uang) + (parseInt(mobil.target) * parseInt(mobil.waktu))) + Math.pow((1 + parseInt(mobil.instrumen) / 100), mobil.waktu);
</script>

<template>
    <Head title="Dashboard" />

    <MainLayout>
        <h1 class="text-title font-bold"> Beli Mobil </h1>
        <hr class="text-transparent h-[3px] my-5 bg-darkorange bg-opacity-20">
        <div class="box-container flex flex-row place-content-evenly items-center my-12">
            <div class="box flex flex-col items-center justify-center w-40">
                <h1 class="text-subheading w-10 h-10 border-2 border-grey flex items-center justify-center text-2xl text-gray font-bold"> 1 </h1>
                <h2 class="pt-2 text-center text-grey"> Perencanaan Pembelian Mobil </h2>
            </div>
            <div class="box flex flex-col items-center justify-center w-40">
                <h1 class="text-subheading w-10 h-10 border-2 border-grey flex items-center justify-center text-2xl text-gray font-bold"> 2 </h1>
                <h2 class="pt-2 text-center text-grey"> Strategi Investasi </h2>
            </div>
            <div class="box flex flex-col items-center justify-center w-40">
                <h1 class="text-title w-16 h-16 bg-darkorange flex items-center justify-center text-2xl text-white font-bold"> 3 </h1>
                <h2 class="pt-2 text-center font-medium"> Ringkasan </h2>
            </div>
        </div>

        <div class="container flex justify-between">
            <div>
                <h1 class="pb-4 text-heading font-bold"> Ringkasan </h1>
                <div class="pb-9">
                    <div class="flex flex-col py-4 bg-yellowtb pl-3 w-[447px]">
                        <h1 class="text-name pb-2 font-semibold"> Total uang yang dibutuhkan sebesar </h1>
                        <h1 class="text-title font-bold text-darkorange"> Rp {{ formatMoney(totalUang) }},00 </h1>
                    </div>
                </div>
                <h1 class="pb-4 text-heading font-bold"> Strategi </h1>
                <div class="">
                    <div class="flex flex-col mb-6 py-4 bg-yellowtb pl-3 w-[447px]">
                        <h1 class="text-name pb-2"> Jumlah uang yang dimiliki saat ini </h1>
                        <h1 class="text-subheading font-medium"> Rp {{ formatMoney(jumlahUang) }},00 </h1>
                    </div>
                    <div class="flex flex-col mb-6 py-4 bg-yellowtb pl-3 w-[447px]">
                        <h1 class="text-name pb-2"> Target investasi (per bulan) </h1>
                        <h1 class="text-subheading font-medium"> Rp {{ formatMoney(targetInvestasi) }},00 </h1>
                    </div>
                    <div class="flex flex-col mb-6 py-4 bg-yellowtb pl-3 w-[447px]">
                        <h1 class="text-name pb-2"> Return investasi </h1>
                        <h1 class="text-subheading font-medium"> {{ returnInvestasi }}% / Tahun </h1>
                    </div>
                    <div class="flex flex-col mb-6 py-4 bg-yellowtb pl-3 w-[447px]">
                        <h1 class="text-name pb-2"> Jumlah periode </h1>
                        <h1 class="text-subheading font-medium"> {{ jumlahPeriode }} Tahun </h1>
                    </div>
                    <div class="flex flex-col mb-6 py-4 bg-yellowtb pl-3 w-[447px]">
                        <h1 class="text-name pb-2"> Hasil investasi </h1>
                        <h1 class="text-subheading font-medium"> Rp {{ formatMoney(hasilInvestasi) }},00 </h1>
                    </div>
                </div>
            </div>
            <img src="../../images/yes.png" class="w-[500px] h-[500px]">
        </div>
        <div class="text-darkorange font-semibold flex flex-row pt-8 pb-20 justify-between">
            <div class="pt-8">
                <Link href="/beliMobil2"> &lt; Sebelumnya </Link>
            </div>
        </div>


    </MainLayout>
</template>
