<template>
  <div class="home">
    <img src="../assets/image.jpg" alt="图片">
    <p>image md5 String: {{ imageMd5 }}</p>
    <p>image md5 to base64: {{ imageBase64 }}</p>
  </div>
</template>

<script>
import MD5 from 'crypto-js/md5'
import Base64 from 'crypto-js/enc-base64'
import ImageFile from '@/assets/image.jpg'

export default {
  name: 'home',
  data () {
    return {
      imageMd5: '',
      imageBase64: ''
    }
  },
  mounted () {
    this.imageMd5 = MD5(ImageFile).toString()
    this.imageBase64 = Base64.stringify(MD5(ImageFile))
    console.log(this.imageMd5)
    console.log(this.imageBase64)
    console.log(MD5(ImageFile).toString(Base64))
  }
}
</script>
