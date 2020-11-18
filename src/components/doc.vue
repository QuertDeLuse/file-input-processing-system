<template>
  <div class="doc-wrapper">
    <div class="doc">
      <div v-if="uploading" class="doc-state">
        <div class="doc-state__img-wrapper">
          <img
            src="@/assets/img/uploading.jpg"
            alt="uploading"
            class="doc-state__img"
          />
        </div>
        <div class="doc-state__group uploading">
          <p class="doc-state__p">Загрузить скан страницы с фотографией</p>
          <p class="doc-state__sub-p">Размер файла не более 5мб</p>
        </div>
      </div>

      <div v-if="checking" class="doc-state">
        <div class="doc-state__img-wrapper">
          <img
            src="@/assets/img/wait.svg"
            alt="uploading"
            class="doc-state__img"
          />
        </div>
        <div class="doc-state__group checking">
          <p class="doc-state__p">Файл загружен</p>
          <p class="doc-state__sub-p">{{ file.name }} ({{ (file.size/1000).toFixed(0) }}КБ)</p>
        </div>
      </div>

      <div v-if="isReady == true && ok == true" class="doc-state">
        <div class="doc-state__img-wrapper">
          <img
            src="@/assets/img/ok.svg"
            alt="uploading"
            class="doc-state__img"
          />
        </div>
        <div class="doc-state__group ok">
          <p class="doc-state__p">Страница с пропиской</p>
          <p class="doc-state__sub-p">{{ file.name }} ({{ (file.size/1000).toFixed(0) }}КБ)</p>
        </div>
      </div>

      <div v-if="isReady == true && ok == false" class="doc-state">
        <div class="doc-state__img-wrapper">
          <img
            src="@/assets/img/upload.svg"
            alt="uploading"
            class="doc-state__img"
          />
        </div>
        <div class="doc-state__group notOk">
          <p class="doc-state__p">Загрузить скан страницы с фотографией</p>
          <p class="doc-state__sub-p">Размер файла не более 5мб</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {

    props: {
        file: File,
    },

  data() {
    return {
      uploading: true,
      checking: false,
      isReady: false,
      ok: false,
    };
  },

  mounted() {
    // console.log(this.file)

    let uploadingTime = Math.floor(Math.random() * Math.floor(3)) * 1000;
    let checkingTime = Math.floor(Math.random() * Math.floor(3)) * 1000;

    setTimeout(() => {
      this.uploading = false;
      this.checking = true;
      
    }, uploadingTime);

    setTimeout(() => {
      this.checking = false;

      this.ok = !!Math.floor(Math.random() * Math.floor(2));
      this.isReady = true;
    }, checkingTime + uploadingTime);
  },
};
</script>

<style lang="scss">
.doc-wrapper {
  margin-top: 30px;
  //   display: flex;
  //   align-items: center;

  .doc {
    .uploading,
    .checking,
    .ok,
    .notOk {
      &:after {
        position: absolute;
        top: 10px;
        right: -100px;
        color: #9c9c9c;
      }
    }
    .uploading {
      &:after {
        content: "Идет загрузка";
      }
    }
    .checking {
      &:after {
        content: "Идет проверка";
      }
    }
    .ok {
      &:after {
        content: "Проверено";
        color: #7fa050;
      }
    }
    .notOk {
      &:after {
        content: "Отклонено";
        color: #c43524;
      }
    }

    .doc-state {
      position: relative;
      display: flex;
      align-items: center;

      .doc-state__img-wrapper {
        display: flex;
        width: 50px;
        height: 50px;
        background-color: #fff;
        align-items: center;
        justify-content: center;
        border-radius: 5px;
        margin-right: 20px;

        .doc-state__img {
        }
      }
      .doc-state__group {
        width: 80%;
        position: relative;

        .doc-state__p,
        .doc-state__sub-p {
          margin: 0;
        }

        .doc-state__p {
        }
        .doc-state__sub-p {
          font-size: 13px;
          color: #9c9c9c;
        }
      }
    }
  }
}
</style>