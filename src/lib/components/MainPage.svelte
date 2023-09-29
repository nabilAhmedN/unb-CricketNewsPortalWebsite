<script>
    import pic1 from '$lib/images/pic1.jpg';
	import pic2 from '$lib/images/pic2.jpg';
	import pic3 from '$lib/images/pic3.jpg';
	import pic4 from '$lib/images/pic4.jpg';
	import pic5 from '$lib/images/pic5.jpg';
</script>

<div>
    <div class="flex flex-col lg:flex-row bg-[#020F2A] px-7 lg:px-4 pt-14 pb-36 gap-4">
        <div class="w-full lg:w-[48%]">
            <a
                href="https://unb.com.bd/category/Bangladesh/youre-the-man-who-brought-glory-for-argentina-pm-tells-emiliano-martinez/118145"
            >
                <img class="rounded-lg img" src={pic1} alt="" />
                <h1 class="text-slate-200 font-bold lg:text-[32px] pt-3">
                    'You're the man who brought glory for Argentina': PM tells Emiliano Martinez
                </h1></a
            >
            <p class="text-slate-200 pt-3 text-xl hidden md:block">
                Goalkeeper of the FIFA World Cup Qatar 2022 winning Argentine team, Emiliano Martinez,
                paid a courtesy call on Prime Minister
            </p>
        </div>
        <div class="flex-1">
            <div class="grid grid-cols-2 gap-4">
                <div>
                    <img src={pic2} alt="" class="rounded-lg" />
                    <p class="mt-2 text-slate-200 text-xs lg:text-xl font-bold pt-3">
                        2022 Football Year Review: A Flashback of the Major Events
                    </p>
                </div>
                <div>
                    <img src={pic3} alt="" class="rounded-lg" />
                    <p class="mt-2 text-slate-200 text-xs lg:text-xl font-bold pt-3">
                        FIFA reviews Salt Bae's 'undue access' to hold World Cup
                    </p>
                </div>
                <div>
                    <img src={pic4} alt="" class="rounded-lg" />
                    <p class="mt-2 text-slate-200 text-xs lg:text-xl font-bold pt-3">
                        FIFA World Cup 2022: Messi’s Records, Argentina’s Road to
                    </p>
                </div>
                <div>
                    <img src={pic5} alt="" class="rounded-lg" />
                    <p class="mt-2 text-slate-200 text-xs lg:text-xl font-bold pt-3">
                        FIFA mostly wins big but loses some trust at Qatar World Cup
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>