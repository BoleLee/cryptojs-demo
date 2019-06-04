<template>
  <div class="home">
    <img src="../assets/image.png" alt="图片" width="200" height="auto">
    <div>
      <h2>public image md5 with CryptoJS</h2>
      <p>{{ publicImage.md5 || '计算中...' }}</p>
      <p>{{ publicImage.base64 || '计算中...' }}</p>
    </div>
    <div>
      <h2>assets image md5 with CryptoJS</h2>
      <p>{{ assetsImage.md5 || '计算中...' }}</p>
      <p>{{ assetsImage.base64 || '计算中...' }}</p>
    </div>
    <div>
      <h2>public image md5 with CLI</h2>
      <p>
        <code>
          md5 public/image.png
        </code>
      </p>
      <p>{{ cli.md5 }}</p>
      <p>
        <code>
          (echo 0:; echo d51877af16db96345e703d3d10898d3a) | xxd -rp -l 16 | base64
        </code>
      </p>
      <p>{{ cli.base64 }}</p>
    </div>
  </div>
</template>

<script>
import MD5 from 'crypto-js/md5'
import Base64 from 'crypto-js/enc-base64'
import assetsImage from '@/assets/image.png'

export default {
  name: 'home',
  data () {
    return {
      publicImage: {},
      assetsImage: {},
      cli: {
        md5: 'd51877af16db96345e703d3d10898d3a',
        base64: '1Rh3rxbbljRecD09EImNOg=='
      }
    }
  },
  mounted () {
    let publicImage = `${process.env.BASE_URL}/image.png`
    this.publicImage = {
      md5: MD5(publicImage).toString(),
      base64: MD5(publicImage).toString(Base64)
    }
    this.assetsImage = {
      md5: MD5(assetsImage).toString(),
      base64: MD5(assetsImage).toString(Base64)
    }
  }
}
</script>
