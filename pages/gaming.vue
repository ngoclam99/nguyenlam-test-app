<script setup lang="ts">
useHead({
  title: 'Gaming Hub - My App',
  meta: [
    { name: 'description', content: 'Trung tâm gaming và esports' }
  ]
})

interface Match {
  id: number
  team1: string
  team2: string
  score: string
  time: string
  status: 'live' | 'upcoming' | 'finished'
}

const liveMatches: Match[] = [
  {
    id: 1,
    team1: 'Team A',
    team2: 'Team B',
    score: '2 - 1',
    time: 'LIVE',
    status: 'live'
  },
  {
    id: 2,
    team1: 'Team C',
    team2: 'Team D',
    score: '1 - 1',
    time: 'LIVE',
    status: 'live'
  },
  {
    id: 3,
    team1: 'Team E',
    team2: 'Team F',
    score: 'vs',
    time: '19:00',
    status: 'upcoming'
  }
]

const news = [
  {
    id: 1,
    title: 'Giải đấu mùa xuân 2024 chính thức khởi tranh',
    image: '🏆',
    date: '24/02/2024'
  },
  {
    id: 2,
    title: 'Top 10 tuyển thủ xuất sắc nhất tháng',
    image: '⭐',
    date: '23/02/2024'
  },
  {
    id: 3,
    title: 'Cập nhật bảng xếp hạng mới nhất',
    image: '📊',
    date: '22/02/2024'
  }
]
</script>

<template>
  <div class="min-h-screen bg-gray-900">
    <!-- Header -->
    <AppHeader />

    <!-- Hero Banner -->
    <section class="bg-gradient-to-r from-yellow-600 to-orange-600 py-20">
      <div class="container mx-auto px-4">
        <div class="max-w-4xl mx-auto text-center">
          <h1 class="text-5xl font-bold text-white mb-6">
            GAMING HUB
          </h1>
          <p class="text-xl text-white/90 mb-8">
            Theo dõi các trận đấu trực tiếp, kết quả và tin tức esports mới nhất
          </p>
          <button class="bg-black text-yellow-500 px-8 py-4 rounded-lg hover:bg-gray-900 transition-colors font-bold text-lg">
            XEM TRỰC TIẾP NGAY
          </button>
        </div>
      </div>
    </section>

    <!-- Live Matches -->
    <section class="py-16 bg-gray-800">
      <div class="container mx-auto px-4">
        <div class="flex items-center justify-between mb-8">
          <h2 class="text-3xl font-bold text-white">
            🔴 TRẬN ĐẤU TRỰC TIẾP
          </h2>
          <a href="#" class="text-yellow-500 hover:text-yellow-400 font-semibold">
            Xem tất cả →
          </a>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div
            v-for="match in liveMatches"
            :key="match.id"
            class="bg-gray-900 rounded-lg p-6 border-2 hover:border-yellow-500 transition-all cursor-pointer"
            :class="{
              'border-red-500': match.status === 'live',
              'border-gray-700': match.status !== 'live'
            }"
          >
            <div class="flex items-center justify-between mb-4">
              <span
                class="px-3 py-1 rounded-full text-xs font-bold"
                :class="{
                  'bg-red-500 text-white animate-pulse': match.status === 'live',
                  'bg-gray-700 text-gray-300': match.status === 'upcoming',
                  'bg-green-500 text-white': match.status === 'finished'
                }"
              >
                {{ match.time }}
              </span>
              <span class="text-yellow-500 text-sm">⚽ BÓNG ĐÁ</span>
            </div>

            <div class="flex items-center justify-between">
              <div class="text-center flex-1">
                <div class="text-white font-bold mb-2">{{ match.team1 }}</div>
                <div class="w-12 h-12 bg-gradient-to-br from-blue-500 to-blue-700 rounded-full mx-auto"></div>
              </div>

              <div class="text-center px-4">
                <div class="text-2xl font-bold text-yellow-500">
                  {{ match.score }}
                </div>
              </div>

              <div class="text-center flex-1">
                <div class="text-white font-bold mb-2">{{ match.team2 }}</div>
                <div class="w-12 h-12 bg-gradient-to-br from-red-500 to-red-700 rounded-full mx-auto"></div>
              </div>
            </div>

            <button class="w-full mt-4 bg-yellow-500 text-black py-2 rounded-lg hover:bg-yellow-400 transition-colors font-bold text-sm">
              XEM TRỰC TIẾP
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- News Section -->
    <section class="py-16 bg-gray-900">
      <div class="container mx-auto px-4">
        <div class="flex items-center justify-between mb-8">
          <h2 class="text-3xl font-bold text-white">
            📰 TIN TỨC MỚI NHẤT
          </h2>
          <a href="#" class="text-yellow-500 hover:text-yellow-400 font-semibold">
            Xem tất cả →
          </a>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div
            v-for="article in news"
            :key="article.id"
            class="bg-gray-800 rounded-lg overflow-hidden hover:transform hover:-translate-y-1 transition-all cursor-pointer"
          >
            <div class="h-48 bg-gradient-to-br from-yellow-600 to-orange-600 flex items-center justify-center text-6xl">
              {{ article.image }}
            </div>
            <div class="p-6">
              <div class="text-gray-400 text-sm mb-2">{{ article.date }}</div>
              <h3 class="text-white font-bold text-lg mb-3">
                {{ article.title }}
              </h3>
              <a href="#" class="text-yellow-500 hover:text-yellow-400 font-semibold text-sm">
                Đọc thêm →
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Stats Section -->
    <section class="py-16 bg-gray-800">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          <div class="text-center">
            <div class="text-5xl font-bold text-yellow-500 mb-2">1000+</div>
            <div class="text-gray-400">Trận đấu</div>
          </div>
          <div class="text-center">
            <div class="text-5xl font-bold text-yellow-500 mb-2">500+</div>
            <div class="text-gray-400">Đội tuyển</div>
          </div>
          <div class="text-center">
            <div class="text-5xl font-bold text-yellow-500 mb-2">50K+</div>
            <div class="text-gray-400">Người dùng</div>
          </div>
          <div class="text-center">
            <div class="text-5xl font-bold text-yellow-500 mb-2">24/7</div>
            <div class="text-gray-400">Trực tiếp</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="bg-black py-8 border-t border-yellow-600/30">
      <div class="container mx-auto px-4">
        <div class="text-center text-gray-400">
          <p>© 2024 Gaming Hub. All rights reserved.</p>
        </div>
      </div>
    </footer>
  </div>
</template>

