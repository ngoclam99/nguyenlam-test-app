<script setup lang="ts">
import { ref } from 'vue'

const isMenuOpen = ref(false)
const activeDropdown = ref<string | null>(null)
const isUserMenuOpen = ref(false)
const isLoggedIn = ref(true) // Set true để hiển thị user menu
const userBalance = ref('1000')
const userName = ref('User')
const isDepositDropdownOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const toggleDropdown = (menu: string) => {
  if (activeDropdown.value === menu) {
    activeDropdown.value = null
  } else {
    activeDropdown.value = menu
  }
}

const closeDropdowns = () => {
  activeDropdown.value = null
  isUserMenuOpen.value = false
  isDepositDropdownOpen.value = false
}

const toggleDepositDropdown = () => {
  isDepositDropdownOpen.value = !isDepositDropdownOpen.value
}

const mainMenuItems = [
  { name: 'LỊCH TRỰC TIẾP', href: '/live', hasDropdown: false },
  { name: 'LỊCH THI ĐẤU', href: '/schedule', hasDropdown: false },
  { name: 'TỶ LỆ CÁ', href: '/odds', hasDropdown: false },
  { name: 'KẾT QUẢ', href: '/results', hasDropdown: false },
  { name: 'PHÒNG CHAT', href: '/chat', hasDropdown: false },
  { name: 'TIN TỨC', href: '/news', hasDropdown: false }
]

const iconMenuItems = [
  { name: 'Bóng Đá', icon: '⚽', href: '/football' },
  { name: 'Nạp Tiền', icon: '�', href: '/deposit' },
  { name: 'Hỗ Trợ', icon: '🎧', href: '/support' },
  { name: 'Bảng Xếp', icon: '�', href: '/rankings' },
  { name: 'Truyền Hình', icon: '�', href: '/tv' },
  { name: 'Tin Tức', icon: '📰', href: '/news' }
]

useHead({
  title: 'Trang chủ - My App',
  link: [
    {
      rel: 'stylesheet',
      href: 'https://fonts.googleapis.com/css2?family=Roboto:wght@400&display=swap'
    }
  ]
})
</script>
<style>
    .logo-box {
        background: black;
        color: white;
        font-size: 60px;
        border-top-right-radius: 60px; /* bo góc */
    }

    /* #menu-nav .group {
        position: relative;
    }

    #menu-nav .group::before {
        content: "";
        position: absolute;
        top: 0;
        left: -10px;
        width: calc(100% + 20px);
        height: 280px;
        background: #d9d9d9;
        border-radius: 20px;
        opacity: 0;
        transition: 0.3s;
        z-index: -1;
    }


    #menu-nav .group:hover::before{
        opacity: 1;
    } */

</style>

<template>
<!-- MOBILE HEADER -->
<header class="lg:hidden bg-[#2B2B2B] shadow-lg font-['Roboto',sans-serif]">
    <div class="flex items-center justify-between px-4 py-3">
        <!-- LOGO -->
        <div class="text-white text-2xl font-bold tracking-wider">
            LOGO
        </div>

        <!-- RIGHT ICONS -->
        <div class="flex items-center gap-3">
            <!-- Search Icon -->
            <button class="text-[#EBC770] text-xl">
                🔍
            </button>

            <!-- User Icon with Badge -->
            <button class="relative text-[#EBC770] text-xl">
                👤
                <span class="absolute -top-1 -right-1 bg-red-500 text-white w-4 h-4 flex items-center justify-center rounded-full text-[10px] font-bold">
                    5
                </span>
            </button>

            <!-- Notification Icon with Badge -->
            <button class="relative text-[#EBC770] text-xl">
                🔔
                <span class="absolute -top-1 -right-1 bg-red-500 text-white w-4 h-4 flex items-center justify-center rounded-full text-[10px] font-bold">
                    3
                </span>
            </button>

            <!-- Hamburger Menu -->
            <button @click="toggleMenu" class="text-[#EBC770] flex flex-col gap-1">
                <span class="w-6 h-0.5 bg-[#EBC770] rounded"></span>
                <span class="w-6 h-0.5 bg-[#EBC770] rounded"></span>
                <span class="w-6 h-0.5 bg-[#EBC770] rounded"></span>
            </button>
        </div>
    </div>

    <!-- MOBILE MENU OVERLAY -->
    <div v-if="isMenuOpen"
         @click="toggleMenu"
         class="fixed inset-0 bg-black/50 z-40">
    </div>

    <!-- MOBILE MENU SIDEBAR -->
    <div :class="['fixed top-0 right-0 h-full w-[280px] bg-[#2B2B2B] z-50 transform transition-transform duration-300', isMenuOpen ? 'translate-x-0' : 'translate-x-full']">
        <div class="p-4">
            <!-- Close Button -->
            <button @click="toggleMenu" class="text-white text-2xl mb-6 float-right">
                ✕
            </button>
            <div class="clear-both"></div>

            <!-- User Info -->
            <div class="text-white mb-6">
                <div class="text-sm mb-2">Xin chào, NguyenVanDen</div>
                <div class="flex items-center gap-2 bg-gradient-to-r from-gray-200 to-gray-100 rounded-full px-3 py-2">
                    <img src="/img/coin.svg" class="w-5 h-5" />
                    <span class="font-bold text-black">1000</span>
                </div>
            </div>

            <!-- Menu Items -->
            <nav class="space-y-2">
                <a href="#" class="block text-[#EBC770] py-2 px-3 rounded hover:bg-[#3B3B3B]">LỊCH TRỰC TIẾP</a>
                <a href="#" class="block text-[#EBC770] py-2 px-3 rounded hover:bg-[#3B3B3B]">LỊCH THI ĐẤU</a>
                <a href="#" class="block text-[#EBC770] py-2 px-3 rounded hover:bg-[#3B3B3B]">TỶ LỆ KÈO</a>
                <a href="#" class="block text-[#EBC770] py-2 px-3 rounded hover:bg-[#3B3B3B]">KẾT QUẢ</a>
                <a href="#" class="block text-[#EBC770] py-2 px-3 rounded hover:bg-[#3B3B3B]">PHÒNG CHAT</a>
                <a href="#" class="block text-[#EBC770] py-2 px-3 rounded hover:bg-[#3B3B3B]">TIN TỨC</a>
            </nav>
        </div>
    </div>
</header>

<!-- DESKTOP HEADER -->
<header class="hidden lg:block bg-black shadow-lg font-['Roboto',sans-serif]">
    <div class="relative mx-auto">

        <!-- LOGO BLOCK -->
        <div class="absolute top-0 left-0 
                    w-[260px] h-[120px]
                    bg-black text-white
                    flex items-center justify-center
                    text-[72px] font-light tracking-widest
                    rounded-tr-[70px]
                    shadow-xl z-30">
            LOGO
        </div>

        <!-- TOP BAR -->
        <div class="bg-[#EBC770] h-[60px] flex items-center pl-[280px] pr-6">
            <!-- MENU -->
            <nav class="flex items-center text-[15px] gap-1 uppercase font-medium tracking-wide">
                <a href="#" class="hover:text-black transition px-4 py-2">Lịch trực tiếp</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Lịch thi đấu</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Tỷ lệ kèo</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Kết quả</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Phòng chat</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Tin tức</a>
            </nav>

            <!-- ACTION BUTTONS -->
            <div class="ml-4 flex items-center gap-2">
                <a href="#"
                   class="px-6 py-2 rounded-full 
                          bg-white text-gray-800 
                          text-sm uppercase font-semibold
                          border border-gray-200
                          hover:bg-gray-100
                          transition duration-200">
                    Đăng ký
                </a>

                <a href="#"
                   class="px-6 py-2 rounded-full 
                          bg-gradient-to-b from-[#4A4A4A] to-black
                          text-[#EBC770]
                          text-sm uppercase font-semibold
                          shadow-md
                          hover:opacity-90
                          transition duration-200">
                    Đăng nhập
                </a>
            </div>
        </div>

        <!-- BOTTOM BAR -->
        <div class="bg-black h-[60px] flex items-center pl-[280px] pr-6">
            <!-- CATEGORY -->
            <div class="flex items-center gap-8">

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/1.svg" class="w-5 h-5" />
                    Bảng Tin
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/2.svg" class="w-5 h-5" />
                    Reels
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/3.svg" class="w-5 h-5" />
                    Highlight
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/4.svg" class="w-5 h-5" />
                    Tip Kèo
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/5.svg" class="w-5 h-5" />
                    Phim Ảnh
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/6.svg" class="w-5 h-5" />
                    Truyện Tranh
                </a>
            </div>

            <!-- RIGHT SIDE -->
            <div class="ml-[50px] flex items-center gap-4">
                <a href="#"
                   class="flex items-center gap-1
                          px-1 py-1 pr-[10px] rounded-full
                          bg-gradient-to-b from-white to-gray-100
                          text-gray-800 text-sm font-medium
                          border border-gray-200
                          hover:bg-gray-200 transition">
                    <img src="/img/7.svg" class="w-7 h-7" />
                    Tiếng Việt
                </a>

                <a href="#" class="flex items-center justify-center pl-[50px]">
                    <img src="/img/8.svg" class="hover:scale-110 transition" />
                </a>

            </div>
        </div>

    </div>
</header>

<br>

<!-- HEADER 2 - DESKTOP -->
<header class="hidden lg:block bg-black shadow-lg font-['Roboto',sans-serif]">
    <div class="relative mx-auto">

        <!-- LOGO BLOCK -->
        <div class="absolute top-0 left-0 
                    w-[260px] h-[120px]
                    bg-black text-white
                    flex items-center justify-center
                    text-[72px] font-light tracking-widest
                    rounded-tr-[70px]
                    shadow-xl z-30">
            LOGO
        </div>

        <!-- TOP BAR -->
        <div class="bg-[#EBC770] h-[70px] flex items-center pl-[280px] pr-6">

            <!-- MENU -->
            <nav class="flex items-center text-[15px] gap-1 uppercase font-medium tracking-wide">
                <a href="#" class="hover:text-black transition px-4 py-2">Lịch trực tiếp</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Lịch thi đấu</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Tỷ lệ kèo</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Kết quả</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Phòng chat</a>
                <a href="#" class="hover:text-black transition px-4 py-2">Tin tức</a>
            </nav>

            <!-- ACTION BUTTONS -->
            <div class="ml-4 flex flex-col items-center">
                <!-- XIN CHÀO -->
                <div class=" text-black text-[12px] font-medium">
                    Xin chào, NguyenVanDen
                </div>

                <div class="flex bg-gradient-to-b from-[#5C5C5C] to-black px-1 py-1 rounded-full">
                    <!-- COIN BOX -->
                    <div class="coin-box-container relative flex items-center
                            bg-gradient-to-r from-gray-200 to-gray-100
                            rounded-full
                            pl-3 pr-3
                            border-2
                            shadow-md gap-4">
                        <span class="font-bold tracking-wide text-black flex items-center gap-1">
                            <img src="/img/coin.svg" class="" />
                            1000
                        </span>

                        <button @click="toggleDepositDropdown"
                                class="ml-3 w-7 h-7 rounded-full
                                    bg-[#EBC770]
                                    flex items-center justify-center
                                    text-lg font-bold text-black
                                    shadow hover:scale-105 transition">
                            +
                        </button>
                    </div>

                    <!-- ICONS -->
                    <div class="ml-2 flex items-center gap-2 text-[#EBC770]">
                        <!-- Bell -->
                        <div class="relative">
                            <img src="/img/bell.svg" class="" />
                            <span class="absolute -top-2 -right-2 
                                        bg-red-500 text-white 
                                        w-3 h-3 flex items-center justify-center
                                        rounded-full font-bold text-[8px] ">
                                10
                            </span>
                        </div>

                        <!-- Mail -->
                        <div class="relative">
                            <img src="/img/Mails.svg" class="" />
                            <span class="absolute -top-2 -right-2 
                                        bg-red-500 text-white
                                        w-3 h-3 flex items-center justify-center
                                        rounded-full font-bold text-[8px]">
                                2
                            </span>
                        </div>

                        <!-- Calendar -->
                        <img src="/img/Diemdanh.svg" class="" />

                    </div>

                    <!-- AVATAR -->
                    <div class="relative group">
                        <img src="/img/User-avatar.svg"
                            class="w-10 h-10 rounded-full border-4 border-[#EBC770] shadow-lg cursor-pointer" />

                        <!-- DROPDOWN -->
                        <div class="absolute right-0 top-full pt-2 w-[250px] z-50
                            opacity-0 invisible pointer-events-none
                            group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                            transition-all duration-300">

                            <div class="bg-[#dadada] px-1 py-1 rounded-xl shadow-lg">
                                <!-- HEADER -->
                                <div class="bg-gradient-to-b from-[#5C5C5C] to-black
                                            text-[#EBC770]
                                            px-4 py-2
                                            rounded-2xl
                                            flex items-center gap-3 shadow-lg">
                                    <img src="/img/Agent.svg" class="w-5 cursor-pointer" />
                                    <span class="font-semibold text-sm tracking-wide">
                                        TRUNG TÂM TÀI KHOẢN
                                    </span>
                                </div>

                                <!-- BODY -->
                                <div class="rounded-b-2xl overflow-hidden text-sm mt-1">
                                    <a href="#" class="flex items-center gap-3 px-5 py-2 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/Home.svg" class="w-5 cursor-pointer" />
                                        <span>TRANG CÁ NHÂN</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/phitieu.svg" class="w-5 cursor-pointer" />
                                        <span>NHIỆM VỤ</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/walet.svg" class="w-5 cursor-pointer" />
                                        <span>VÍ CỦA BẠN</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/Chart4.svg" class="w-5 cursor-pointer" />
                                        <span>LỊCH SỬ GIAO DỊCH</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/logout.svg" class="w-5 cursor-pointer" />
                                        <span>THOÁT TÀI KHOẢN</span>
                                    </a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- BOTTOM BAR -->
        <div class="bg-black h-[60px] flex items-center pl-[280px] pr-6">

            <!-- CATEGORY -->
            <div class="flex items-center gap-8">

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/1.svg" class="w-5 h-5" />
                    Bảng Tin
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/2.svg" class="w-5 h-5" />
                    Reels
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/3.svg" class="w-5 h-5" />
                    Highlight
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/4.svg" class="w-5 h-5" />
                    Tip Kèo
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/5.svg" class="w-5 h-5" />
                    Phim Ảnh
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/6.svg" class="w-5 h-5" />
                    Truyện Tranh
                </a>
            </div>

            <!-- RIGHT SIDE -->
            <div class="ml-[50px] flex items-center gap-4">
                <a href="#"
                   class="flex items-center gap-1
                          px-1 py-1 pr-[10px] rounded-full
                          bg-gradient-to-b from-white to-gray-100
                          text-gray-800 text-sm font-medium
                          border border-gray-200
                          hover:bg-gray-200 transition">
                    <img src="/img/7.svg" class="w-7 h-7" />
                    Tiếng Việt
                </a>

                <a href="#" class="flex items-center justify-center pl-[40px] ml-14">
                    <img src="/img/8.svg" class="hover:scale-110 transition" />
                </a>

            </div>
        </div>

    </div>
</header>
<br>

<!-- HEADER 3 - DESKTOP (with dropdown menus) -->
<header class="hidden lg:block bg-black shadow-lg font-['Roboto',sans-serif]">
    <div class="relative mx-auto">

        <!-- LOGO BLOCK -->
        <div class="absolute top-0 left-0 
                    w-[260px] h-[120px]
                    bg-black text-white
                    flex items-center justify-center
                    text-[72px] font-light tracking-widest
                    rounded-tr-[70px]
                    shadow-xl z-30">
            LOGO
        </div>

        <!-- TOP BAR -->
        <div class="bg-[#EBC770] h-[70px] flex items-center pl-[280px] pr-6">

            <!-- MENU -->
            <nav class="flex items-center gap-1 text-[15px] uppercase font-medium tracking-wide" id="menu-nav">
                <div class="relative group">
                    <a href="#" class="block px-4 py-2 rounded-full
                        group-hover:bg-black group-hover:text-[#F8E889] transition-all duration-300">
                        <span class="">Lịch trực tiếp</span>
                    </a>

                    <!-- DROPDOWN -->
                    <div class="absolute left-0 top-full z-50 w-[150px]
                        opacity-0 invisible pointer-events-none
                        group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                        transition-all duration-300">

                        <div class="bg-[#D9D9D9] rounded-2xl shadow-xl p-2">
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-100">
                                <img src="/img/ani_Soccer.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG ĐÁ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-150">
                                <img src="/img/ani_Duabi.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">ĐUA BI</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-200">
                                <img src="/img/basketball.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG RỔ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-[250ms]">
                                <img src="/img/ani_Gamepad.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">E-SPORTS</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-300">
                                <img src="/img/ani_Casino.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">CASINO</span>
                            </a>
                        </div>
                    </div>
                </div>
                <!-- LỊCH THI ĐẤU -->
                <div class="relative group">
                    <a href="#" class="block px-4 py-2 rounded-full
                        group-hover:bg-black group-hover:text-[#F8E889] transition-all duration-300">
                        <span>Lịch thi đấu</span>
                    </a>

                    <div class="absolute left-0 top-full z-50 w-[150px]
                        opacity-0 invisible pointer-events-none
                        group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                        transition-all duration-300">

                        <div class="bg-[#D9D9D9] rounded-2xl shadow-xl p-2">
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-100">
                                <img src="/img/ani_Soccer.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG ĐÁ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-150">
                                <img src="/img/ani_Duabi.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">ĐUA BI</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-200">
                                <img src="/img/basketball.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG RỔ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-[250ms]">
                                <img src="/img/ani_Gamepad.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">E-SPORTS</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-300">
                                <img src="/img/ani_Casino.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">CASINO</span>
                            </a>
                        </div>
                    </div>
                </div>

                <!-- TỶ LỆ KÈO -->
                <div class="relative group">
                    <a href="#" class="block px-4 py-2 rounded-full
                        group-hover:bg-black group-hover:text-[#F8E889] transition-all duration-300">
                        <span>Tỷ lệ kèo</span>
                    </a>

                    <div class="absolute left-0 top-full z-50 w-[150px]
                        opacity-0 invisible pointer-events-none
                        group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                        transition-all duration-300">

                        <div class="bg-[#D9D9D9] rounded-2xl shadow-xl p-2">
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-100">
                                <img src="/img/ani_Soccer.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG ĐÁ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-150">
                                <img src="/img/ani_Duabi.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">ĐUA BI</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-200">
                                <img src="/img/basketball.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG RỔ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-[250ms]">
                                <img src="/img/ani_Gamepad.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">E-SPORTS</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-300">
                                <img src="/img/ani_Casino.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">CASINO</span>
                            </a>
                        </div>
                    </div>
                </div>

                <!-- KẾT QUẢ -->
                <div class="relative group">
                    <a href="#" class="block px-4 py-2 rounded-full
                        group-hover:bg-black group-hover:text-[#F8E889] transition-all duration-300">
                        <span>Kết quả</span>
                    </a>

                    <div class="absolute left-0 top-full z-50 w-[150px]
                        opacity-0 invisible pointer-events-none
                        group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                        transition-all duration-300">

                        <div class="bg-[#D9D9D9] rounded-2xl shadow-xl p-2">
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-100">
                                <img src="/img/ani_Soccer.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG ĐÁ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-150">
                                <img src="/img/ani_Duabi.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">ĐUA BI</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-200">
                                <img src="/img/basketball.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG RỔ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-[250ms]">
                                <img src="/img/ani_Gamepad.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">E-SPORTS</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-300">
                                <img src="/img/ani_Casino.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">CASINO</span>
                            </a>
                        </div>
                    </div>
                </div>

                <!-- PHÒNG CHAT -->
                <div class="relative group">
                    <a href="#" class="block px-4 py-2 rounded-full
                        group-hover:bg-black group-hover:text-[#F8E889] transition-all duration-300">
                        <span>Phòng chat</span>
                    </a>

                    <div class="absolute left-0 top-full z-50 w-[150px]
                        opacity-0 invisible pointer-events-none
                        group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                        transition-all duration-300">

                        <div class="bg-[#D9D9D9] rounded-2xl shadow-xl p-2">
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-100">
                                <img src="/img/ani_Soccer.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG ĐÁ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-150">
                                <img src="/img/ani_Duabi.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">ĐUA BI</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-200">
                                <img src="/img/basketball.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG RỔ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-[250ms]">
                                <img src="/img/ani_Gamepad.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">E-SPORTS</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-300">
                                <img src="/img/ani_Casino.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">CASINO</span>
                            </a>
                        </div>
                    </div>
                </div>

                <!-- TIN TỨC -->
                <div class="relative group">
                    <a href="#" class="block px-4 py-2 rounded-full
                        group-hover:bg-black group-hover:text-[#F8E889] transition-all duration-300">
                        <span>Tin tức</span>
                    </a>

                    <div class="absolute left-0 top-full z-50 w-[150px]
                        opacity-0 invisible pointer-events-none
                        group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                        transition-all duration-300">

                        <div class="bg-[#D9D9D9] rounded-2xl shadow-xl p-2">
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-100">
                                <img src="/img/ani_Soccer.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG ĐÁ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-150">
                                <img src="/img/ani_Duabi.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">ĐUA BI</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-200">
                                <img src="/img/basketball.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">BÓNG RỔ</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-[250ms]">
                                <img src="/img/ani_Gamepad.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">E-SPORTS</span>
                            </a>
                            <a href="#" class="flex items-center gap-3 px-2 py-2 rounded-xl bg-[#ffffff17] hover:bg-[#ffffff30] transition mb-1
                                opacity-0 translate-y-[-10px]
                                group-hover:opacity-100 group-hover:translate-y-0
                                transition-all duration-300 delay-300">
                                <img src="/img/ani_Casino.svg" class="w-6 h-6 rounded-full" />
                                <span class="text-sm">CASINO</span>
                            </a>
                        </div>
                    </div>
                </div>
            </nav>

            <!-- ACTION BUTTONS -->
            <div class="ml-4 flex flex-col items-center">
                <!-- XIN CHÀO -->
                <div class=" text-black text-[12px] font-medium">
                    Xin chào, NguyenVanDen
                </div>

                <div class="flex bg-gradient-to-b from-[#5C5C5C] to-black px-1 py-1 rounded-full">
                    <!-- COIN BOX -->
                    <div class="coin-box-container relative flex items-center bg-gradient-to-r from-gray-200 to-gray-100 rounded-full pl-3 pr-3 border-2 shadow-md gap-2">
                        <span class="font-bold tracking-wide text-black flex items-center gap-1">
                            <img src="/img/coin.svg" class="" />
                            1000
                        </span>

                        <div class="box-momo"></div>

                        <button @click="toggleDepositDropdown"
                                class="ml-3 w-7 h-7 rounded-full
                                    bg-[#EBC770]
                                    flex items-center justify-center
                                    text-lg font-bold text-black
                                    shadow hover:scale-105 transition">
                            {{ isDepositDropdownOpen ? '×' : '+' }}
                        </button>

                        <!-- DROPDOWN NẠP TIỀN -->
                        <div v-if="isDepositDropdownOpen"
                             class="absolute top-full right-0 mt-2 w-[100%] z-50
                                    bg-[#00000024] backdrop-blur-md
                                    rounded-3xl shadow-2xl p-2 shadow-xl">

                            <!-- Item 1: 1000 -->
                            <div class="flex items-center justify-between px-1 py-1 mb-1
                                        rounded-2xl transition cursor-pointer  bg-[#0000001A]">
                                <div class="flex items-center gap-1">
                                    <img src="/img/iconnap.svg" class="w-5 h-5" />
                                    <span class="text-black font-bold text-[17px] px-2">20.000</span>
                                </div>
                            </div>

                            <div class="flex items-center justify-between px-1 py-1 mb-1
                                        rounded-2xl transition cursor-pointer  bg-[#0000001A]">
                                <div class="flex items-center gap-1">
                                    <img src="/img/KG.svg" class="w-5 h-5" />
                                    <span class="text-black font-bold text-[17px] px-2">20.000</span>
                                </div>
                            </div>

                            <!-- Nút Nạp thêm -->
                            <div class="w-full flex items-center justify-center gap-2 mt-10">
                                <button class="bg-gradient-to-b from-[#EBC770] to-[#D4A850]
                                           text-black font-bold py-1 px-2 
                                           flex items-center justify-center gap-2
                                           transition shadow-md rounded-full">
                                <span class="text-xs">+</span>
                                </button>
                                <span>Nạp tiền</span>
                             </div>
                        </div>
                    </div>

                    <!-- ICONS -->
                    <div class="ml-2 flex items-center gap-2 text-[#EBC770]">
                        <!-- Bell -->
                        <div class="relative">
                            <img src="/img/bell.svg" class="" />
                            <span class="absolute -top-2 -right-2 
                                        bg-red-500 text-white 
                                        w-3 h-3 flex items-center justify-center
                                        rounded-full font-bold text-[8px] ">
                                10
                            </span>
                        </div>

                        <!-- Mail -->
                        <div class="relative">
                            <img src="/img/Mails.svg" class="" />
                            <span class="absolute -top-2 -right-2 
                                        bg-red-500 text-white
                                        w-3 h-3 flex items-center justify-center
                                        rounded-full font-bold text-[8px]">
                                2
                            </span>
                        </div>

                        <!-- Calendar -->
                        <img src="/img/Diemdanh.svg" class="" />

                    </div>

                    <!-- AVATAR -->
                    <div class="relative group">
                        <img src="/img/User-avatar.svg"
                            class="w-10 h-10 rounded-full border-4 border-[#EBC770] shadow-lg cursor-pointer" />

                        <!-- DROPDOWN -->
                        <div class="absolute right-0 top-full pt-2 w-[250px] z-50
                            opacity-0 invisible pointer-events-none
                            group-hover:opacity-100 group-hover:visible group-hover:pointer-events-auto
                            transition-all duration-300">

                            <div class="bg-[#dadada] px-1 py-1 rounded-xl shadow-lg">
                                <!-- HEADER -->
                                <div class="bg-gradient-to-b from-[#5C5C5C] to-black
                                            text-[#EBC770]
                                            px-4 py-2
                                            rounded-2xl
                                            flex items-center gap-3 shadow-lg">
                                    <img src="/img/Agent.svg" class="w-5 cursor-pointer" />
                                    <span class="font-semibold text-sm tracking-wide">
                                        TRUNG TÂM TÀI KHOẢN
                                    </span>
                                </div>

                                <!-- BODY -->
                                <div class="rounded-b-2xl overflow-hidden text-sm mt-1">
                                    <a href="#" class="flex items-center gap-3 px-5 py-2 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/Home.svg" class="w-5 cursor-pointer" />
                                        <span>TRANG CÁ NHÂN</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/phitieu.svg" class="w-5 cursor-pointer" />
                                        <span>NHIỆM VỤ</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/walet.svg" class="w-5 cursor-pointer" />
                                        <span>VÍ CỦA BẠN</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/Chart4.svg" class="w-5 cursor-pointer" />
                                        <span>LỊCH SỬ GIAO DỊCH</span>
                                    </a>

                                    <a href="#" class="flex items-center gap-3 px-5 py-3 transition bg-[#ffffff17] hover:bg-[#ffffff30] rounded-2xl mb-1">
                                        <img src="/img/logout.svg" class="w-5 cursor-pointer" />
                                        <span>THOÁT TÀI KHOẢN</span>
                                    </a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- BOTTOM BAR -->
        <div class="bg-black h-[60px] flex items-center pl-[280px] pr-6">

            <!-- CATEGORY -->
            <div class="flex items-center gap-8">

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/1.svg" class="w-5 h-5" />
                    Bảng Tin
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/2.svg" class="w-5 h-5" />
                    Reels
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/3.svg" class="w-5 h-5" />
                    Highlight
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/4.svg" class="w-5 h-5" />
                    Tip Kèo
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/5.svg" class="w-5 h-5" />
                    Phim Ảnh
                </a>

                <a href="#" class="flex items-center gap-2 
                                   bg-gradient-to-b from-[#F8E889] to-[#E4B764] 
                                   bg-clip-text text-transparent 
                                   text-[15px] font-medium
                                   hover:opacity-80 transition">
                    <img src="/img/6.svg" class="w-5 h-5" />
                    Truyện Tranh
                </a>
            </div>

            <!-- RIGHT SIDE -->
            <div class="ml-[50px] flex items-center gap-4">
                <a href="#"
                   class="flex items-center gap-1
                          px-1 py-1 pr-[10px] rounded-full
                          bg-gradient-to-b from-white to-gray-100
                          text-gray-800 text-sm font-medium
                          border border-gray-200
                          hover:bg-gray-200 transition">
                    <img src="/img/7.svg" class="w-7 h-7" />
                    Tiếng Việt
                </a>

                <a href="#" class="flex items-center justify-center pl-[40px] ml-14">
                    <img src="/img/8.svg" class="hover:scale-110 transition" />
                </a>

            </div>
        </div>

    </div>
</header>
</template>

