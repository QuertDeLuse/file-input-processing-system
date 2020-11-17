<template>
  <div id="app" class="app">
    <div class="container">
      <div class="one-col-grid">
        <div class="grid-item">
          <div class="col-6 ml-3">
            <div class="doc-loader-wrapper">
              <form class="doc-loader">
                <div class="acc-confirmation-wrapper">
                  <h3 class="acc-confirmation_heading">
                    Подтверждение аккаунта
                  </h3>
                  <p class="acc-confirmation_text">
                    Для подтверждения вашего аккаунта вам нужно заполнить все
                    поля, подтвердить почтовый ящик и телефон, а также загрузить
                    сканы ваших документов.
                  </p>
                </div>
                <DocSend @updateFiles="files = $event" />
                <Doc v-for="file in files" :key="file.id" v-bind:file="file"/>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import DocSend from "@/components/docSend";
import Doc from "@/components/doc";

export default {
  name: "App",
  components: {
    DocSend,
    Doc,
  },

  data() {
    return {
      files: [],
    }
  },

  methods: {

  },
};
</script>

<style lang="scss">
html {
  box-sizing: border-box;
  overflow: auto;
}
*,
*:before,
*:after {
  box-sizing: inherit;
}
body {
  margin: 0;
  padding: 0;
  overflow: auto;
  overflow-x: hidden;
  font-family: "PT Sans", sans-serif;
}
.container {
  width: 90%;
  max-width: 1092px;
  margin-left: auto;
  margin-right: auto;

  @media screen and (max-width: 859px) {
    width: 100%;
    max-width: 819px;
    padding: 0px 20px;
  }

  .grid-item {
    padding: 0px 6px;

    @media screen and (max-width: 859px) {
      padding: 0px 4.5px;
    }

    .col-2 {
      width: 16.6666667%;
    }

    .col-6 {
      width: 50%;
    }

    .col-8 {
      width: 66.6666667%;
    }

    .ml-3 {
      margin-left: 25%;
    }

    .ml-2 {
      margin-left: 16.6666667%;
    }

    .ml-none-tablet {
      @media screen and (max-width: 600px) {
        margin-left: 0%;
      }
    }

    .col-1-tablet {
      @media screen and (max-width: 600px) {
        width: 100%;
      }
    }
  }

  .one-col-grid,
  .two-col-grid,
  .three-col-grid,
  .four-col-grid,
  .five-col-grid,
  .six-col-grid {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
  }

  .one-col-grid {
    .grid-item {
      width: 100%;
    }
  }

  .two-col-grid {
    .grid-item {
      width: 50%;
    }
  }

  .three-col-grid {
    .grid-item {
      width: 33.3333%;
    }
  }

  .four-col-grid {
    .grid-item {
      width: 25%;
    }
  }

  .five-col-grid {
    .grid-item {
      width: 20%;
    }
  }

  .six-col-grid {
    .grid-item {
      width: 16.6666667%;
    }
  }

  .one-col-grid-tablet {
    @media screen and (max-width: 600px) {
      .grid-item {
        width: 100%;
      }
    }
  }

  .two-col-grid-tablet {
    @media screen and (max-width: 600px) {
      .grid-item {
        width: 50%;
      }
    }
  }

  .hidden-block-tablet {
    @media screen and (max-width: 600px) {
      display: none;
    }
  }
}
.app {
  background-color: #f7f7f7;
  min-height: 100vh;
}

.doc-loader-wrapper {
  margin-top: 100px;

  .doc-loader {
    .acc-confirmation-wrapper {
      .acc-confirmation_heading {
        font-size: 16px;
        font-weight: bold;
        color: #333;
      }
      .acc-confirmation_text {
        font-size: 13px;
        color: #9c9c9c;
      }
    }
  }
}
</style>
