<template>
  <div>
    <h2>Image uploader</h2>
    <div
      class="np-image-upload-picker"
      v-if="imageFile == null || imageFile.length == 0"
    >
      Select an image file:
      <input type="file" @change="showImagePreview($event)" accept="image/*" />
    </div>
    <div
      class="np-image-preview"
      v-if="imageFile != null && imageFile.length != 0"
    >
      <img class="np-preview" :src="imageFile" />
    </div>
    <div v-if="imageFile != null && imageFile.length != 0 && !isImageUploading">
      <button @click="clearImage" class="np-upload-btn np-upload-btn-cancel">
        Cancel
      </button>
      <button @click="uploadImage" class="np-upload-btn np-upload-btn-confirm">
        Upload
      </button>
    </div>
    <div class="np-upload-in-progress" v-if="isImageUploading">
      Please wait while your file is being uploaded ...
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageUploader",
  data() {
    return {
      imageFile: null,
      input: null,
      isImageUploading: false,
    };
  },
  methods: {
    showImagePreview(event) {
      this.input = event.target;
      if (this.input.files && this.input.files[0]) {
        let reader = new FileReader();
        reader.onload = (e) => {
          this.imageFile = e.target.result;
        };
        reader.readAsDataURL(this.input.files[0]);
      }
    },
    uploadImage() {
      this.isImageUploading = true;
      setTimeout(() => {
        console.log(this.imageFile);
        this.isImageUploading = false;
        this.clearImage();
        alert("Image uploaded sucessfully!");
      }, 3000);
    },
    clearImage() {
      this.imageFile = null;
      this.input = null;
    },
  },
};
</script>

<style scoped>
.np-image-preview {
  padding: 20px;
  background: #eee;
  border-radius: 16px;
  margin: 10px;
}

.np-image-upload-picker {
  padding: 20px;
  background: #eee;
  border-radius: 16px;
  margin: 10px;
}

img.np-preview {
  background-color: #fff;
  border: 1px solid #ddd;
  padding: 5px;
  height: 200px;
  border-radius: 16px;
  margin: 10px;
}
.np-upload-btn {
  margin: 10px;
  border: 0px !important;
  font-size: 18px;
  padding: 16px 60px !important;
  font-weight: 300;
  color: #fff;
  border-radius: 30px;
}

.np-upload-btn-confirm {
  background: rgb(0, 163, 73) !important;
}

.np-upload-btn-cancel {
  background: rgb(122, 0, 31) !important;
}

.np-upload-in-progress {
  background: #eee !important;
  margin: 10px;
  border: 0px !important;
  font-size: 18px;
  padding: 16px 60px !important;
  font-weight: 300;
  color: #000;
  border-radius: 30px;
}
</style>
