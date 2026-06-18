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
        <p class="eyebrow">Приглашение на свадьбу</p>

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

    <section class="section intro" v-reveal>
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

          <div class="intro-carousel">
            <transition name="intro-collage" mode="out-in">
              <div :key="activeIntroSlide" class="intro-carousel__slide">
                <img
                  v-if="currentIntroSlide[0]"
                  class="intro-carousel__photo intro-carousel__photo--wide"
                  :src="`${baseUrl}images/intro-carousel/${currentIntroSlide[0]}`"
                  alt="Савелий и Василина"
                >

                <img
                  v-if="currentIntroSlide[1]"
                  class="intro-carousel__photo intro-carousel__photo--large"
                  :src="`${baseUrl}images/intro-carousel/${currentIntroSlide[1]}`"
                  alt="Савелий и Василина"
                >

                <img
                  v-if="currentIntroSlide[2]"
                  class="intro-carousel__photo intro-carousel__photo--small"
                  :src="`${baseUrl}images/intro-carousel/${currentIntroSlide[2]}`"
                  alt="Савелий и Василина"
                >
              </div>
            </transition>

            <div class="intro-carousel__dots">
              <button
                v-for="(_, index) in introCarouselSlides"
                :key="index"
                class="intro-carousel__dot"
                :class="{ 'is-active': index === activeIntroSlide }"
                type="button"
                @click="activeIntroSlide = index"
              ></button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section
      class="section wishes"
      v-reveal
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

          <h2>СЮРПРИЗЫ</h2>

          <p>
            Мы всегда ценим и любим креатив, поэтому если у вас возникло желание сделать 
            что-то особенное для нас, вы можете обратиться к нашему ведущему для воплощения своих идей!<br>
            Артем  +<span class="wishes-date__number">7-922-440-87-80</span>
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

    <section class="section dresscode" v-reveal>
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

    <section class="section schedule" v-reveal>
      <h2>Программа дня</h2>

      <div class="schedule-list">
        <div
          v-for="(item, index) in scheduleItems"
          :key="`${item.time}-${item.title}`"
          class="schedule-item"
          v-reveal
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


    <!-- <section id="rsvp" class="section rsvp" v-reveal>
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
    </section> -->

    <section id="rsvp" class="section rsvp" v-reveal>
      <h2>Анкета гостя</h2>

      <p>
        Пожалуйста, заполните короткую анкету, чтобы мы могли всё правильно подготовить.
      </p>

      <form class="rsvp-form" @submit.prevent="submitRsvp">
        <div class="rsvp-card">
          <label class="rsvp-label" for="guestName">
            Ваше Имя и Фамилия
          </label>

          <input
            id="guestName"
            v-model.trim="rsvpForm.guestName"
            class="rsvp-input"
            type="text"
            placeholder="Мой ответ"
            required
          >
        </div>

        <div class="rsvp-card">
          <p class="rsvp-question">
            Есть ли у Вас особые предпочтения по еде?
          </p>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.food"
              type="radio"
              value="нет"
              required
            >
            <span class="rsvp-radio__control"></span>
            <span>нет</span>
          </label>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.food"
              type="radio"
              value="вегетарианец"
            >
            <span class="rsvp-radio__control"></span>
            <span>вегетарианец</span>
          </label>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.food"
              type="radio"
              value="аллергия"
            >
            <span class="rsvp-radio__control"></span>
            <span>аллергия, укажу в поле «Другое»</span>
          </label>

          <label class="rsvp-radio rsvp-radio--other">
            <input
              v-model="rsvpForm.food"
              type="radio"
              value="Другое"
            >
            <span class="rsvp-radio__control"></span>
            <span>Другое:</span>

            <input
              v-model.trim="rsvpForm.foodOther"
              class="rsvp-inline-input"
              type="text"
              :disabled="rsvpForm.food !== 'Другое' && rsvpForm.food !== 'аллергия'"
            >
          </label>
        </div>

        <div class="rsvp-card">
          <p class="rsvp-question">
            Какой алкоголь Вы предпочитаете?
          </p>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.alcohol"
              type="radio"
              value="Красное вино"
              required
            >
            <span class="rsvp-radio__control"></span>
            <span>Красное вино</span>
          </label>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.alcohol"
              type="radio"
              value="Белое вино"
            >
            <span class="rsvp-radio__control"></span>
            <span>Белое вино</span>
          </label>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.alcohol"
              type="radio"
              value="Игристое"
            >
            <span class="rsvp-radio__control"></span>
            <span>Игристое</span>
          </label>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.alcohol"
              type="radio"
              value="Виски/коньяк"
            >
            <span class="rsvp-radio__control"></span>
            <span>Виски/коньяк</span>
          </label>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.alcohol"
              type="radio"
              value="Водка"
            >
            <span class="rsvp-radio__control"></span>
            <span>Водка</span>
          </label>

          <label class="rsvp-radio">
            <input
              v-model="rsvpForm.alcohol"
              type="radio"
              value="Не буду пить алкоголь"
            >
            <span class="rsvp-radio__control"></span>
            <span>Не буду пить алкоголь</span>
          </label>

          <label class="rsvp-radio rsvp-radio--other">
            <input
              v-model="rsvpForm.alcohol"
              type="radio"
              value="Другое"
            >
            <span class="rsvp-radio__control"></span>
            <span>Другое (пожелания, если вы не пьете алкоголь):</span>

            <input
              v-model.trim="rsvpForm.alcoholOther"
              class="rsvp-inline-input"
              type="text"
              :disabled="rsvpForm.alcohol !== 'Другое'"
            >
          </label>
        </div>

        <div class="rsvp-card">
          <label class="rsvp-label" for="comment">
            Комментарий
          </label>

          <textarea
            id="comment"
            v-model.trim="rsvpForm.comment"
            class="rsvp-textarea"
            placeholder="Напишите, если хотите что-то добавить"
          ></textarea>
        </div>

        <button
          class="button rsvp-submit"
          type="submit"
          :disabled="!canSubmitRsvp"
        >
          {{ isSubmittingRsvp ? 'Отправляем...' : 'Отправить ответ' }}
        </button>

        <p v-if="rsvpSuccess" class="rsvp-message rsvp-message--success">
          Спасибо! Ваш ответ отправлен.
        </p>

        <p v-if="rsvpError" class="rsvp-message rsvp-message--error">
          Не получилось отправить ответ. Попробуйте ещё раз.
        </p>
      </form>
    </section>

    <section class="section wait-block" v-reveal>
      <div class="wait-title">
        <span class="wait-title__text">Мы ждём</span>
        <span class="wait-title__letter">В</span>
        <span class="wait-title__tail">ас</span>
      </div>

      <div class="wait-calendar">
        <h2 class="wait-calendar__month">Август</h2>

        <div class="wait-calendar__grid">
          <span></span><span></span><span></span><span></span><span></span>
          <span>1</span><span>2</span>
          <span>3</span><span>4</span><span>5</span><span>6</span><span>7</span><span>8</span><span>9</span>
          <span>10</span><span>11</span><span>12</span><span>13</span><span>14</span>
          <span class="wait-calendar__day--wedding">
            <span class="wait-calendar__heart"></span>
            <span class="wait-calendar__day-number">15</span>
          </span>
          <span>16</span>
          <span>17</span><span>18</span><span>19</span><span>20</span><span>21</span><span>22</span><span>23</span>
          <span>24</span><span>25</span><span>26</span><span>27</span><span>28</span><span>29</span><span>30</span>
          <span>31</span>
        </div>
      </div>
    </section>

    <section class="section map" v-reveal>
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
    <section class="section finale" v-reveal>
      <h2 class="finale__title">
        До скорой<br>
        встречи!
      </h2>

      <div class="finale__wave" aria-hidden="true"></div>

      <div class="finale__love" aria-hidden="true">
        <span>With</span>
        <span>Love</span>
      </div>

      <p class="finale__names">
        Савелий &amp; Василина
      </p>
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

const dressCodeExamplesImage = `${baseUrl}images/dresscode/outfits-example.png`

import TimelineIcon from './components/TimelineIcon.vue'

const scheduleItems = [
  {
    time: '14:00',
    icon: 'rings',
    title: 'Встреча и регистрация в ЗАГСе',
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
    description: 'Церемония, ужин, поздравления, музыка и самые тёплые слова в кругу близких.',
  },
  {
    time: '23:00',
    icon: 'fireworks',
    title: 'Завершение вечера',
    description: 'Хорошая финальная точка и ещё один красивый момент нашего праздника.',
  },
]

const googleFormEmbedUrl = 'https://docs.google.com/forms/d/e/1FAIpQLSdAeL8jQOzYEjBQjs_YMtZn7bnD8SyrgwnXRHe8uwJphFouVw/viewform?embedded=true'
const googleFormUrl = 'https://docs.google.com/forms/d/e/1FAIpQLSdAeL8jQOzYEjBQjs_YMtZn7bnD8SyrgwnXRHe8uwJphFouVw/viewform'

import { computed, onMounted, onUnmounted, reactive, ref } from 'vue'

const heroImageUrl = `${baseUrl}images/hero.jpg`
const formsparkActionUrl = 'https://submit-form.com/3WHoUhppQ'
const rsvpForm = reactive({
  guestName: '',
  food: '',
  foodOther: '',
  alcohol: '',
  alcoholOther: '',
  comment: '',
})

const isSubmittingRsvp = ref(false)
const rsvpSuccess = ref(false)
const rsvpError = ref(false)

const introCarouselImages = [
  'photo-1.jpg',
  'photo-2.jpg',
  'photo-3.jpg',
  'photo-4.jpg',
  'photo-5.jpg',
  'photo-6.jpg',
]

const activeIntroSlide = ref(0)

const introCarouselSlides = computed(() => {
  const slides = []

  for (let index = 0; index < introCarouselImages.length; index += 3) {
    slides.push(introCarouselImages.slice(index, index + 3))
  }

  return slides
})

const currentIntroSlide = computed(() => {
  return introCarouselSlides.value[activeIntroSlide.value] || []
})

let introCarouselTimer = null

const canSubmitRsvp = computed(() => {
  const hasName = rsvpForm.guestName.length > 0
  const hasFood = rsvpForm.food.length > 0
  const hasAlcohol = rsvpForm.alcohol.length > 0

  const hasFoodOther =
    rsvpForm.food !== 'Другое' && rsvpForm.food !== 'аллергия'
      ? true
      : rsvpForm.foodOther.length > 0

  const hasAlcoholOther =
    rsvpForm.alcohol !== 'Другое'
      ? true
      : rsvpForm.alcoholOther.length > 0

  return (
    hasName &&
    hasFood &&
    hasAlcohol &&
    hasFoodOther &&
    hasAlcoholOther &&
    !isSubmittingRsvp.value
  )
})

function getFoodAnswer() {
  if (rsvpForm.food === 'Другое' || rsvpForm.food === 'аллергия') {
    return rsvpForm.foodOther
  }

  return rsvpForm.food
}

function getAlcoholAnswer() {
  if (rsvpForm.alcohol === 'Другое') {
    return rsvpForm.alcoholOther
  }

  return rsvpForm.alcohol
}

async function submitRsvp() {
  if (!canSubmitRsvp.value) {
    return
  }

  isSubmittingRsvp.value = true
  rsvpSuccess.value = false
  rsvpError.value = false

  try {
    const response = await fetch(formsparkActionUrl, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        Accept: 'application/json',
      },
      body: JSON.stringify({
        'Имя и фамилия': rsvpForm.guestName,
        'Предпочтения по еде': getFoodAnswer(),
        'Предпочитаемый алкоголь': getAlcoholAnswer(),
        'Комментарий': rsvpForm.comment || '—',
        'Дата отправки': new Date().toLocaleString('ru-RU'),
        _email: {
          subject: `Анкета гостя: ${rsvpForm.guestName}`,
        },
      }),
    })

    if (!response.ok) {
      throw new Error(`Formspark error: ${response.status}`)
    }

    rsvpSuccess.value = true

    rsvpForm.guestName = ''
    rsvpForm.food = ''
    rsvpForm.foodOther = ''
    rsvpForm.alcohol = ''
    rsvpForm.alcoholOther = ''
    rsvpForm.comment = ''
  } catch (error) {
    console.error('Ошибка отправки формы:', error)
    rsvpError.value = true
  } finally {
    isSubmittingRsvp.value = false
  }
}

const vReveal = {
  mounted(el) {
    el.classList.add('reveal')

    const observer = new IntersectionObserver(
      ([entry]) => {
        if (entry.isIntersecting) {
          el.classList.add('is-visible')
          return
        }

        const rect = el.getBoundingClientRect()
        const viewportHeight = window.innerHeight || document.documentElement.clientHeight
        const isFarFromViewport = rect.bottom < -120 || rect.top > viewportHeight + 120

        if (isFarFromViewport) {
          el.classList.remove('is-visible')
        }
      },
      {
        threshold: 0.12,
        rootMargin: '0px 0px -12% 0px',
      }
    )

    observer.observe(el)
    el._revealObserver = observer
  },

  unmounted(el) {
    el._revealObserver?.disconnect()
  },
}

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

  if (!window.matchMedia('(pointer: coarse)').matches) {
    window.addEventListener('wheel', speedUpWheelScroll, { passive: false })
  }
  introCarouselTimer = setInterval(() => {
  activeIntroSlide.value =
      (activeIntroSlide.value + 1) % introCarouselSlides.value.length
  }, 4500)
})

onUnmounted(() => {
  clearTimeout(copiedTimer)
  clearInterval(countdownTimer)

  window.removeEventListener('wheel', speedUpWheelScroll)
  clearInterval(introCarouselTimer)
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

function speedUpWheelScroll(event) {
  const ignoredTags = ['INPUT', 'TEXTAREA', 'SELECT', 'BUTTON']

  if (ignoredTags.includes(event.target.tagName)) {
    return
  }

  event.preventDefault()
  window.scrollBy({
    top: event.deltaY * 1.45,
    behavior: 'auto', // <-- мгновенный прыжок
  })
}
</script>