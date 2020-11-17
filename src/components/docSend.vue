<template>
  <div class="send-doc-wrapper">
    <div class="send-doc__upload-btn-wrapper">
      <img
        src="@/assets/img/upload.svg"
        class="send-doc__upload-btn"
        alt="upload"
      />
    </div>

    <div class="send-doc__input-group">
      <input @change="previewFiles" type="file" multiple name="file" id="file" class="send-doc__input" />
      <label for="file" class="send-doc__label"
        >Загрузить скан страницы с фотографией</label
      >
      <label for="file" class="send-doc__sub-label"
        >Размер файла не более 5мб</label
      >
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            
        }
    },

    methods: {
        previewFiles(event) {
            // console.log( event.target.files)
            this.$emit('updateFiles', event.target.files);
        }
    }

};
</script>

<style lang="scss">
.send-doc-wrapper {
  display: flex;
  align-items: center;

  .send-doc__upload-btn-wrapper {
    display: flex;
    width: 50px;
    height: 50px;
    background-color: #fff;
    align-items: center;
    justify-content: center;
    border-radius: 5px;
    margin-right: 20px;

    .send-doc__upload-btn {
    }
  }
  .send-doc__input-group {
    width: 80%;
    position: relative;    

    .send-doc__input {
      cursor: pointer;
      width: 100%;
      position: relative;
      z-index: -2;
    //   opacity: 0.1;
    }

    .send-doc__label {
      cursor: pointer;
      //   width: 100%;
      position: absolute;
      left: 0px;
      z-index: 1;

      border-bottom: 1px solid #858585;
    }
    .send-doc__sub-label {
      font-size: 13px;
      color: #9c9c9c;
    }
  }
}
</style>