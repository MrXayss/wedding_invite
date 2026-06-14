<template>
  <main class="page">
    <transition name="toast">
      <div v-if="copied" class="toast">
        Ссылка скопирована
      </div>
    </transition>
    <section
      class="hero"
      :style="{ '--hero-image': `url('${heroImageUrl}')` }"
    >
      <div class="hero__content">
        <p class="eyebrow">Приглашаем на свадьбу</p>

        <h1>Савелий & Василина</h1>

        <p class="hero__text">
          Будем счастливы разделить<br>
          этот незабываемый день с вами
        </p>

        <p class="date">
          <span class="date__number">15</span>
          <span class="date__month">августа</span>
          <span class="date__number">2026</span>
        </p>

        <div class="countdown">
          <div
            v-for="item in countdownItems"
            :key="item.label"
            class="countdown__item"
          >
            <span class="countdown__value">{{ item.value }}</span>
            <span class="countdown__label">{{ item.label }}</span>
          </div>
        </div>
      </div>
    </section>

    <section class="section intro">
      <div class="intro-card">
        <div class="intro-card__top"></div>

        <div class="intro-card__body">
          <h2 class="intro-card__title">
            <span>Дорогой</span>
            <span>Гость!</span>
          </h2>

          <p class="intro-card__text">
            Мы рады сообщить Вам, что состоится самое
            главное торжество в нашей жизни — день нашей свадьбы!
            Приглашаем Вас разделить с нами
            радость этого незабываемого дня.
          </p>

          <div class="intro-card__image">
            <img
              :src="`${baseUrl}images/intro-couple.jpg`"
              alt="Савелий и Василина"
            >
          </div>
        </div>
      </div>
    </section>

    <section
      class="section wishes"
      :style="{ '--wishes-bg': `url('${baseUrl}images/wishes-bg.jpg')` }"
    >
      <div class="wishes-card">
        <div class="wishes-card__content">
          <h2>Пожелания по подаркам</h2>

          <p>
            Ваше присутствие в день нашей свадьбы — самый значимый подарок для нас!
          </p>

          <p>
            Мы понимаем, что дарить цветы на свадьбу — это традиция,
            но мы не сможем насладиться их красотой в полной мере...
            Будем рады любой другой альтернативе: вино или в денежном эквиваленте.
          </p>

          <h2>Примечание</h2>

          <p>
            Будем благодарны, если вы воздержитесь от криков «Горько» на празднике,
            ведь поцелуй — это знак выражения чувств, он не может быть по заказу.
          </p>

          <h2>Подтверждение</h2>

          <p>
            Пожалуйста, подтвердите своё присутствие до
            <span class="wishes-date">
              <span class="wishes-date__number">01</span>
              <span class="wishes-date__text">июля</span>
              <span class="wishes-date__number">2026</span>
            </span>
          </p>
        </div>
      </div>
    </section>

    <section class="section dresscode">
      <h2>Дресс-код</h2>

      <div class="dresscode-title-divider">
        <span>❦</span>
      </div>

      <p>
        Нам будет приятно, если вы поддержите цветовую палитру праздника
      </p>

      <div class="dresscode-groups">
        <div class="dresscode-group">
          <h3><span>Для мужчин</span></h3>

          <div class="dresscode-icons">
            <img
              v-for="image in dressCodeMenImages"
              :key="image"
              :src="`${baseUrl}images/dresscode/${image}`"
              alt="Пример дресс-кода для мужчин"
            >
          </div>
        </div>

        <div class="dresscode-divider"></div>

        <div class="dresscode-group">
          <h3><span>Для леди</span></h3>

          <div class="dresscode-icons">
            <img
              v-for="image in dressCodeWomenImages"
              :key="image"
              :src="`${baseUrl}images/dresscode/${image}`"
              alt="Пример дресс-кода для леди"
            >
          </div>
        </div>
      </div>

      <div class="dresscode-examples">
        <img
          :src="dressCodeExamplesImage"
          alt="Примеры нарядов для дресс-кода"
        >
      </div>
    </section>

    <section class="section schedule">
      <h2>Программа дня</h2>

      <div class="schedule-list">
        <div
          v-for="(item, index) in scheduleItems"
          :key="`${item.time}-${item.title}`"
          class="schedule-item"
        >
          <div class="schedule-item__time">
            {{ item.time }}
          </div>

          <div class="schedule-item__center">
            <div class="schedule-item__circle">
              <TimelineIcon :name="item.icon" />
            </div>

            <div
              v-if="index !== scheduleItems.length - 1"
              class="schedule-item__line"
            ></div>
          </div>

          <div class="schedule-item__content">
            <h3>{{ item.title }}</h3>
            <p>{{ item.description }}</p>

            <a
              v-if="item.link"
              :href="item.link"
              class="schedule-item__link"
              target="_blank"
              rel="noopener noreferrer"
            >
              {{ item.linkText }}
            </a>
          </div>
        </div>
      </div>
    </section>


    <section id="rsvp" class="section rsvp">
      <h2>Подтвердите присутствие</h2>

      <p>
        Пожалуйста, заполните короткую форму ниже, чтобы мы могли всё правильно подготовить.
      </p>

      <div class="form-wrapper">
        <iframe
          :src="googleFormEmbedUrl"
          title="Форма подтверждения присутствия"
          width="100%"
          height="1000"
          frameborder="0"
          marginheight="0"
          marginwidth="0"
          loading="lazy"
        >
          Загрузка…
        </iframe>
      </div>

      <a
        class="form-link"
        :href="googleFormUrl"
        target="_blank"
        rel="noopener noreferrer"
      >
        Открыть форму в отдельной вкладке
      </a>
    </section>

    <section class="section map">
      <h2>Как добраться</h2>

      <p>
        Ждём вас по адресу: г.Сургут, ул. Мелик-Карамова, 38.
      </p>

      <div class="map-wrapper">
        <iframe
          src="https://yandex.ru/map-widget/v1/?um=constructor%3A1b3fe93e80b619b8ab3dfde1cca78091b02d9cad65f4a3f6e23833d3aa6a8b92&amp;source=constructor"
          width="100%"
          height="420"
          frameborder="0"
          allowfullscreen
        ></iframe>
      </div>

      <a
        class="button button--secondary"
        href="https://yandex.ru/maps/-/CPtLjC-I"
        target="_blank"
      >
        Открыть в Яндекс Картах
      </a>
    </section>
  </main>
</template>

<script setup>
const baseUrl = import.meta.env.BASE_URL
const dressCodeMenImages = [
  'men-1.png',
  'men-2.png',
  'men-3.png',
  'men-4.png',
  'men-5.png',
]

const dressCodeWomenImages = [
  'women-1.png',
  'women-2.png',
  'women-3.png',
  'women-4.png',
  'women-5.png',
]

const dressCodeExamplesImage = `${baseUrl}images/dresscode/outfits-example.jpg`

import TimelineIcon from './components/TimelineIcon.vue'

const scheduleItems = [
  {
    time: '14:00',
    icon: 'rings',
    title: 'Регистрация в ЗАГСе',
    description: 'Самый трогательный момент нашего дня. Приглашаются все гости.',
  },
  {
    time: '16:30',
    icon: 'glasses',
    title: 'Сбор гостей в ресторане',
    description: 'Будем рады видеть вас на площадке. Время для тёплых встреч и приветственного настроения.',
  },
  {
    time: '17:00',
    icon: 'dinner',
    title: 'Свадебный ужин',
    description: 'Ужин, поздравления, музыка и самые тёплые слова в кругу близких.',
  },
  {
    time: '23:00',
    icon: 'fireworks',
    title: 'Окончание вечера',
    description: 'Хорошее завершение вечера и ещё один красивый момент нашего праздника.',
  },
]

const googleFormEmbedUrl = 'https://docs.google.com/forms/d/e/1FAIpQLSdAeL8jQOzYEjBQjs_YMtZn7bnD8SyrgwnXRHe8uwJphFouVw/viewform?embedded=true'
const googleFormUrl = 'https://docs.google.com/forms/d/e/1FAIpQLSdAeL8jQOzYEjBQjs_YMtZn7bnD8SyrgwnXRHe8uwJphFouVw/viewform'

import { computed, onMounted, onUnmounted, ref } from 'vue'

const heroImageUrl = `${baseUrl}images/hero.jpg`

const copied = ref(false)
const now = ref(new Date())

const weddingDate = new Date('2026-08-15T16:30:00+05:00')

let copiedTimer = null
let countdownTimer = null

const countdownItems = computed(() => {
  const diff = Math.max(0, weddingDate.getTime() - now.value.getTime())
  const totalSeconds = Math.floor(diff / 1000)

  const days = Math.floor(totalSeconds / 86400)
  const hours = Math.floor((totalSeconds % 86400) / 3600)
  const minutes = Math.floor((totalSeconds % 3600) / 60)
  const seconds = totalSeconds % 60

  return [
    {
      value: String(days).padStart(2, '0'),
      label: 'дней',
    },
    {
      value: String(hours).padStart(2, '0'),
      label: 'часов',
    },
    {
      value: String(minutes).padStart(2, '0'),
      label: 'минут',
    },
    {
      value: String(seconds).padStart(2, '0'),
      label: 'секунд',
    },
  ]
})

onMounted(() => {
  countdownTimer = setInterval(() => {
    now.value = new Date()
  }, 1000)
})

onUnmounted(() => {
  clearTimeout(copiedTimer)
  clearInterval(countdownTimer)
})

async function copyText(text) {
  try {
    await navigator.clipboard.writeText(text)

    copied.value = true

    clearTimeout(copiedTimer)

    copiedTimer = setTimeout(() => {
      copied.value = false
    }, 2500)
  } catch (error) {
    console.error('Ошибка копирования:', error)
  }
}

</script>