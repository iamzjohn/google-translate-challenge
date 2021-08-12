<template>
  <div>
    <div class="flex">
      <button
        class="border border-blue-500 w-12 h-12 rounded-full flex items-center justify-center bg-blue-500 text-white mr-4">
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
          class="border border-blue-500 w-16 h-16 rounded-full flex items-center justify-center bg-blue-500 text-white">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                  d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4"/>
          </svg>
        </button>
      </div>

      <div class="w-full flex py-4 px-8 relative -mt-8">
        <div class="border border-gray-300 w-1/2 -mr-1 flex items-center px-4 rounded-l-full"
             style="border-radius: 50px 60px 0 50px;">
          <span class="text-blue-500 mr-2 border-b border-blue-500 pb-3 -mb-2">Detect Language</span>
          <span v-for="item in languages.slice(0, 3)" class="text-gray-300 mx-2 pb-1">{{ item }}</span>
        </div>
        <div id="curved-corner-bottomleft"></div>
        <div class="border border-gray-300 w-1/2 -ml-1 flex items-center px-4 rounded-l-full"
             style="border-radius: 57px 50px 50px 0;">
          <span
            v-for="(item, index) in languages.slice(0, 4)"
            :class="{'text-gray-300 pb-1': index !== 0, 'text-blue-500 border-b border-blue-500 pb-3 -mb-2': index === 0}"
            class=" mx-2"
          >
            {{ item }}
          </span>
        </div>

      </div>

      <div class="px-8 font-normal">
        <div class="w-full flex rounded-xl border border-gray-300">
          <div class="w-1/2 relative px-6">
            <textarea class="w-full mb-12 textarea--disable-resize textarea--height py-2 text-gray-500 focus:border-transparent focus:outline-none"
                      :class="textareClassNames" v-model="textareaValue"></textarea>
            <div class="w-full absolute bottom-0 h-16 flex items-center justify-between -ml-6 px-6">
              <div class="flex items-center text-gray-400">
                <button>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-6 hover:text-blue-500">
                    <g fill="none">
                      <path d="M0 0h24v24H0z"/>
                      <path d="M0 0h24v24H0z"/>
                      <path d="M0 0h24v24H0z"/>
                    </g>
                    <path fill="currentColor"
                          d="M12 14c1.66 0 3-1.34 3-3V5c0-1.66-1.34-3-3-3S9 3.34 9 5v6c0 1.66 1.34 3 3 3z"/>
                    <path fill="currentColor"
                          d="M17 11c0 2.76-2.24 5-5 5s-5-2.24-5-5H5c0 3.53 2.61 6.43 6 6.92V21h2v-3.08c3.39-.49 6-3.39 6-6.92h-2z"/>
                  </svg>
                </button>
                <button class="mx-4">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-6 hover:text-blue-500">
                    <path d="M0 0h24v24H0V0z" fill="none"/>
                    <path fill="currentColor"
                          d="M3 9v6h4l5 5V4L7 9H3zm7-.17v6.34L7.83 13H5v-2h2.83L10 8.83zM16.5 12A4.5 4.5 0 0014 7.97v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77 0-4.28-2.99-7.86-7-8.77z"/>
                  </svg>
                </button>
                <button>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-6 fill-current hover:text-blue-500">
                    <path
                      d="M20 5H4c-1.1 0-1.99.9-1.99 2L2 17c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm-9 3h2v2h-2V8zm0 3h2v2h-2v-2zM8 8h2v2H8V8zm0 3h2v2H8v-2zm-1 2H5v-2h2v2zm0-3H5V8h2v2zm9 7H8v-2h8v2zm0-4h-2v-2h2v2zm0-3h-2V8h2v2zm3 3h-2v-2h2v2zm0-3h-2V8h2v2z"/>
                    <path d="M0 0h24v24H0zm0 0h24v24H0z" fill="none"/>
                  </svg>
                </button>
              </div>
              <div class="text-right text-gray-400">
                {{ wordCount }}/2000
              </div>
            </div>
          </div>

          <div class="w-1/2 relative text-white bg-blue-500 rounded-xl">
            <p class="w-full mb-10 textarea--disable-resize textarea--height p-6">
              {{ translatedContent }}
            </p>
            <div class="w-full absolute bottom-0 h-16 flex items-center justify-between px-6">
              <div class="w-1/2 flex items-center">
                <button>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-6">
                    <path d="M0 0h24v24H0V0z" fill="none"/>
                    <path fill="currentColor"
                          d="M3 9v6h4l5 5V4L7 9H3zm7-.17v6.34L7.83 13H5v-2h2.83L10 8.83zM16.5 12A4.5 4.5 0 0014 7.97v8.05c1.48-.73 2.5-2.25 2.5-4.02zM14 3.23v2.06c2.89.86 5 3.54 5 6.71s-2.11 5.85-5 6.71v2.06c4.01-.91 7-4.49 7-8.77 0-4.28-2.99-7.86-7-8.77z"/>
                  </svg>
                </button>
              </div>
              <div class="w-1/2 flex items-center justify-end">
                <button>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-5">
                    <path d="M0 0h24v24H0z" fill="none"/>
                    <path
                      fill="currentColor"
                      d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"/>
                  </svg>
                </button>
                <button class="mx-4">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-5">
                    <path d="M0 0h24v24H0z" fill="none"/>
                    <path
                      fill="currentColor"
                      d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04a.996.996 0 000-1.41l-2.34-2.34a.996.996 0 00-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"/>
                  </svg>
                </button>
                <button>
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-5">
                    <path d="M0 0h24v24H0z" fill="none"/>
                    <path
                      fill="currentColor"
                      d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm-1 4l6 6v10c0 1.1-.9 2-2 2H7.99C6.89 23 6 22.1 6 21l.01-14c0-1.1.89-2 1.99-2h7zm-1 7h5.5L14 6.5V12z"/>
                  </svg>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="flex items-center justify-end py-4 p-8">

        <button class="border border-gray-300 w-12 h-12 rounded-full flex items-center justify-center text-blue-500">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6">
            <path d="M0 0h24v24H0z" fill="none"/>
            <path
              fill="currentColor"
              d="M13 3a9 9 0 00-9 9H1l3.89 3.89.07.14L9 12H6c0-3.87 3.13-7 7-7s7 3.13 7 7-3.13 7-7 7c-1.93 0-3.68-.79-4.94-2.06l-1.42 1.42A8.954 8.954 0 0013 21a9 9 0 000-18zm-1 5v5l4.28 2.54.72-1.21-3.5-2.08V8H12z"/>
          </svg>
        </button>

        <button
          class="border border-gray-300 w-12 h-12 rounded-full flex items-center justify-center text-blue-500 mx-4">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6">
            <path d="M0 0h24v24H0z" fill="none"/>
            <path fill="currentColor"
                  d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/>
          </svg>
        </button>

        <button class="border border-gray-300 w-12 h-12 rounded-full flex items-center justify-center text-blue-500">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6">
            <path d="M0 0h24v24H0z" fill="none"/>
            <path
              fill="currentColor"
              d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5c-1.66 0-3 1.34-3 3s1.34 3 3 3zm-8 0c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5C6.34 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/>
          </svg>
        </button>

      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'LanguagePicker',
    data: () => ({
      textareaValue: ''
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
      textareClassNames () {
        const classNames = {}
        classNames['pointer-events-none cursor-not-allowed'] = this.wordCount >= 2000

        return classNames
      },
      wordCount () {
        return this.textareaValue.length
      },
      translatedContent() {
        // TODO, replace with API calls to really translate the content
        return this.textareaValue
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

  .textarea--height {
    min-height: 15em;
  }

  .textarea--disable-resize {
    resize: none;
  }
</style>