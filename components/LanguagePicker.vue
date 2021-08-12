<template>
  <div>
    <div class="flex">
      <button
        class="border border-blue-500 w-12 h-12 rounded-full flex items-center justify-center bg-blue-500 text-white mr-4"
      >
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M3 5h12M9 3v2m1.048 9.5A18.022 18.022 0 016.412 9m6.088 9h7M11 21l5-10 5 10M12.751 5C11.783 10.77 8.07 15.61 3 18.129"/>
        </svg>
      </button>

      <button class="border border-gray-300 w-12 h-12 rounded-full flex items-center justify-center text-blue-500">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
          <path fill-rule="evenodd"
                d="M4 4a2 2 0 012-2h4.586A2 2 0 0112 2.586L15.414 6A2 2 0 0116 7.414V16a2 2 0 01-2 2H6a2 2 0 01-2-2V4z"
                clip-rule="evenodd"/>
        </svg>
      </button>
    </div>

    <div class="mt-4 text-base font-medium">
      <div class="w-full flex justify-center">
        <button
          class="border border-blue-500 w-16 h-16 rounded-full flex items-center justify-center bg-blue-500 text-white"
          @click="swapLanguages()"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4"/>
          </svg>
        </button>
      </div>

      <div class="w-full flex py-4 px-8 relative -mt-8">
        <div class="border border-gray-300 w-1/2 -mr-1 flex items-center px-4 rounded-l-full"
             style="border-radius: 50px 55px 0 50px;">
          <button
            class="mr-2"
            :class="{'text-gray-300 pb-1': !autoDetectActivated, 'text-blue-500 border-b border-blue-500 pb-3 -mb-2': autoDetectActivated}"
            @click="resetAutoDetect()"
          >
            Detect Language
          </button>

          <button
            v-for="(item, index) in languages.slice(0, 3)"
            :key="index"
            class="mx-2"
            :class="{'text-gray-300 pb-1': !isActiveFromLang(item), 'text-blue-500 border-b border-blue-500 pb-3 -mb-2': isActiveFromLang(item)}"
            @click="setFromLanguage(item)"
          >
            {{ item }}
          </button>
        </div>
        <div id="curved-corner-bottomleft"></div>
        <div class="border border-gray-300 w-1/2 -ml-1 flex items-center px-4 rounded-l-full"
             style="border-radius: 51px 50px 50px 0;">
          <button
            v-for="(item, index) in languages.slice(0, 4)"
            :key="index"
            :class="{'text-gray-300 pb-1': !isActiveToLang(item), 'text-blue-500 border-b border-blue-500 pb-3 -mb-2': isActiveToLang(item)}"
            class=" mx-2"
            @click="setToLanguage(item)"
          >
            {{ item }}
          </button>
        </div>

      </div>

    </div>
  </div>
</template>

<script>
  export default {
    name: 'LanguagePicker',
    data: () => ({
      autoDetect: true,
      fromLanguage: 'English',
      toLanguage: 'English'
    }),
    computed: {
      languages () {
        return [
          'English',
          'Spanish',
          'Arabic',
          'French',
          'Italian',
          'Portuguese'
        ]
      },
      autoDetectActivated() {
        return this.autoDetect
      }
    },
    methods: {
      resetAutoDetect() {
        this.autoDetect = true
        this.fromLanguage = 'English'
      },
      setFromLanguage(lang) {
        this.fromLanguage = lang
        this.autoDetect = false
      },
      setToLanguage(lang) {
        this.toLanguage = lang
      },
      isActiveFromLang(lang) {
        if(this.autoDetect) return false
        return this.fromLanguage === lang
      },
      isActiveToLang(lang) {
        return this.toLanguage === lang
      },
      swapLanguages() {
        const tempTo = this.toLanguage
        this.toLanguage = this.fromLanguage
        this.fromLanguage = tempTo

        // TODO also swap the content from translated and what the user added
      }
    }
  }
</script>

<style scoped>
  #curved-corner-bottomleft {
    width: 4em;
    height: 3em;
    overflow: hidden;
    position: relative;
    border-bottom: 1px #d1d5db solid;
  }

  #curved-corner-bottomleft:before {
    content: "";
    display: block;
    width: 110%;
    height: 130%;
    position: absolute;
    border-radius: 45%;
    bottom: 20px;
    left: -4px;
    box-shadow: -30px 60px 0 50px white;
    border-width: 0 0 2px 0;
    border-color: #d1d5db;
  }
</style>