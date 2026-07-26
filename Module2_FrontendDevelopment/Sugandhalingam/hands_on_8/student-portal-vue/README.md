# Student Portal — Vue 3

Vue 3 + Composition API implementation of the Student Portal, using `<script setup>`,
Vue Router, and Pinia (setup-store style).

## Setup

```bash
npm install
npm run dev
```

Open the printed local URL (defaults to http://localhost:5173).

## Structure

```
src/
  components/
    Header.vue         -> nav links + enrolled-count badge from the Pinia store
    CourseCard.vue      -> presentational, props: name/code/credits/grade, has a <slot>
  views/
    HomeView.vue         -> route: '/'
    CoursesView.vue       -> route: '/courses' — reactive courses list, search, enroll
    CourseDetailView.vue  -> route: '/courses/:id' — useRoute()/useRouter()
    ProfileView.vue        -> route: '/profile' — enrolled list + total credits
  router/index.js         -> all 4 routes + a beforeEach navigation-log guard
  stores/enrollment.js     -> Pinia store: enrolledCourses, totalCredits, enroll(), unenroll()
  data/courses.js           -> static 5-course catalog shared by Courses/Detail views
```

## What each task demonstrates

**Components & reactive data**
- `CourseCard.vue` is a single-file component with `<script setup>` + `defineProps` for
  `name`, `code`, `credits`, `grade`.
- `CoursesView.vue` holds `courses = ref([])`, populated inside `onMounted` (here via a
  short `setTimeout` to also demonstrate a `isLoading` state, similar to a real fetch).
- `v-for="course in courses" :key="course.id"` renders a `CourseCard` per course, using
  `:name="course.name"` etc. for prop binding.
- `filteredCourses` is a `computed()` filtering on a `searchTerm` ref, bound to the search
  input with `v-model`.

**Vue Router**
- `src/router/index.js` defines all four routes, including the dynamic `/courses/:id`.
- `App.vue` renders `<Header />` (which contains the `RouterLink`s) and `<RouterView />`.
- `CourseDetailView.vue` reads the `id` param with `useRoute()` and looks the course up
  from the shared catalog.
- Clicking "Enroll and go to profile" calls `useRouter().push('/profile')`.
- `router.beforeEach` logs `Navigating to: <path>` before every route change.

**Pinia**
- `src/stores/enrollment.js` is a setup-style store (`defineStore('enrollment', () => {...})`)
  with `enrolledCourses` (ref), `totalCredits` (computed), and `enroll` / `unenroll` actions.
- `CoursesView.vue` and `CourseDetailView.vue` both call `store.enroll(course)`.
- `ProfileView.vue` lists `store.enrolledCourses` and shows `store.totalCredits`.
- `Header.vue` shows `store.enrolledCourses.length` as a live badge.
- Install the Vue DevTools browser extension, open the Pinia tab, and enroll a course to
  watch the state update in real time.
