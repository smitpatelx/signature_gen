<template>
  <div class="w-full min-h-screen bg-white p-6 flex flex-wrap style-inputs bg-white">
    <Header/>
    <form method="post" @submit.prevent class="w-full md:w-1/2 min-h-screen bg-gray-100 py-6 px-8 rounded-l-md shadow-2xl ring-1 ring-gray-300">
      <h1 class="text-2xl font-semibold">Generate your signature</h1>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="name" class="w-full text-gray-600 text-sm">Full Name</label>
        <input type="text" id="name" v-model="name" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded" required>
      </div>
      <div class="w-full grid grid-cols-2 gap-3 mt-3">
        <div class="w-full flex flex-col">
          <label for="position" class="w-full text-gray-600 text-sm">Position</label>
          <input type="text" id="position" v-model="position" class="w-full text-gray-500 mt-1 px-3 py-1 text-base rounded" required>
        </div>
        <div class="w-full flex flex-col">
          <label for="company_name" class="w-full text-gray-600 text-sm">Company Name</label>
          <input type="text" id="company_name" v-model="company_name" class="w-full text-gray-500 mt-1 px-3 py-1 text-base rounded" required>
        </div>
      </div>
      <div class="w-full grid grid-cols-1 md:grid-cols-2 gap-3 mt-3">
        <div class="w-full flex flex-col">
          <label for="email" class="w-full text-gray-600 text-sm">Email</label>
          <input type="email" id="email" v-model="email" class="w-full text-gray-500 mt-1 px-3 py-1 text-base rounded" required>
        </div>
        <div class="w-full flex flex-col">
          <label for="phone" class="w-full text-gray-600 text-sm">Phone</label>
          <div class="flex flex-row justify-start content-start items-stretch mt-1">
            <div class="bg-gray-200 text-gray-700 rounded-l px-3 py-1 flex justify-center items-center flex-grow-0">+1</div>
            <input type="tel" id="phone" v-model="phone" class="text-gray-500 px-3 py-1 text-base rounded-r flex-grow flex-1">
          </div>
        </div>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="img_url" class="w-full text-gray-600 text-sm">Image Url</label>
        <input type="url" id="img_url" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded" v-model="img_url" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="website" class="w-full text-gray-600 text-sm">Website</label>
        <input type="url" id="website" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded" v-model="website" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="banner_url" class="w-full text-gray-600 text-sm">Banner</label>
        <input type="url" id="banner_url" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded" v-model="banner_url" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="banner_url_target" class="w-full text-gray-600 text-sm">Banner Url Target</label>
        <input type="url" id="banner_url_target" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded" v-model="banner_url_target" required>
      </div>
      <h2 class="text-2xl font-semibold text-gray-900 mt-8">Social:</h2>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="linkedin" class="w-full text-gray-600 text-sm">Linkedin Url</label>
        <input type="url" id="linkedin" v-model="linkedin_url" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="twitter" class="w-full text-gray-600 text-sm">Twitter Url</label>
        <input type="url" id="twitter" v-model="twitter_url" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded">
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="instagram" class="w-full text-gray-600 text-sm">Instagram Url</label>
        <input type="url" id="instagram" v-model="instagram_url" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded">
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="facebook" class="w-full text-gray-600 text-sm">Facebook Page Url</label>
        <input type="url" id="facebook" v-model="facebook_url" class="w-full md:w-2/3 text-gray-500 mt-1 px-3 py-1 text-base rounded">
      </div>
      <div class="w-full mt-8 pr-8 flex flex-wrap justify-between">
        <button type="reset">
          Reset
        </button>
      </div>
    </form>
    <div class="w-full md:w-1/2 min-h-screen bg-gray-200 py-6 px-8 flex flex-wrap flex-col items-start rounded-r-md ring-1 ring-gray-300">
      <h1 class="text-2xl font-semibold text-gray-900 mb-3">Output:</h1>
      <div class="w-full bg-white py-5 px-3 rounded scrolling-touch overflow-x-scroll lg:overflow-x-hidden signature" v-html="template" />
      <div class="w-full mt-8 pr-8 flex flex-wrap justify-between">
        <button type="button" @click="copy()">
          Copy 
          <svg class="inline-block h-4 w-4 m-2 fill-current" viewBox="0 0 24 24"><path fill-rule="evenodd" clip-rule="evenodd" d="M11 10c-.5523 0-1 .4477-1 1v9c0 .5523.4477 1 1 1h9c.5523 0 1-.4477 1-1v-9c0-.5523-.4477-1-1-1h-9zm-3 1c0-1.6569 1.3431-3 3-3h9c1.6569 0 3 1.3431 3 3v9c0 1.6569-1.3431 3-3 3h-9c-1.6569 0-3-1.3431-3-3v-9z" /><path fill-rule="evenodd" clip-rule="evenodd" d="M4 3a1 1 0 00-1 1v9a1 1 0 001 1h1c.5523 0 1 .4477 1 1s-.4477 1-1 1H4a3 3 0 01-3-3V4a3 3 0 013-3h9a3 3 0 013 3v1c0 .5523-.4477 1-1 1s-1-.4477-1-1V4a1.0002 1.0002 0 00-1-1H4z"/></svg>
        </button>
        <button type="button" v-clipboard:copy="template">
          Copy Html 
          <svg class="inline-block h-4 w-4 m-2 fill-current" viewBox="0 0 24 24"><path d="M11.553 1.106a1 1 0 01.894 0l10 5a1 1 0 010 1.788l-10 5a1 1 0 01-.894 0l-10-5a1 1 0 010-1.788l10-5zM4.236 7L12 10.882 19.764 7 12 3.118 4.236 7zM1.106 16.553a1 1 0 011.341-.447L12 20.882l9.553-4.776a1 1 0 11.894 1.788l-10 5a1 1 0 01-.894 0l-10-5a1 1 0 01-.447-1.341z"/><path d="M1.106 11.553a1 1 0 011.341-.447L12 15.882l9.553-4.776a1 1 0 11.894 1.788l-10 5a1 1 0 01-.894 0l-10-5a1 1 0 01-.447-1.341z"/></svg>
        </button>
      </div>

      <h1 class="text-2xl font-semibold text-gray-900 mt-4 mb-3">Dark Version:</h1>
      <div class="w-full py-5 px-3 rounded scrolling-touch overflow-x-scroll lg:overflow-x-hidden signature" style="background: #333;" v-html="template2" />
      <div class="w-full mt-8 pr-8 flex flex-wrap justify-between">
        <button type="button" @click="copy2()">
          Copy 
          <svg class="inline-block h-4 w-4 m-2 fill-current" viewBox="0 0 24 24"><path fill-rule="evenodd" clip-rule="evenodd" d="M11 10c-.5523 0-1 .4477-1 1v9c0 .5523.4477 1 1 1h9c.5523 0 1-.4477 1-1v-9c0-.5523-.4477-1-1-1h-9zm-3 1c0-1.6569 1.3431-3 3-3h9c1.6569 0 3 1.3431 3 3v9c0 1.6569-1.3431 3-3 3h-9c-1.6569 0-3-1.3431-3-3v-9z" /><path fill-rule="evenodd" clip-rule="evenodd" d="M4 3a1 1 0 00-1 1v9a1 1 0 001 1h1c.5523 0 1 .4477 1 1s-.4477 1-1 1H4a3 3 0 01-3-3V4a3 3 0 013-3h9a3 3 0 013 3v1c0 .5523-.4477 1-1 1s-1-.4477-1-1V4a1.0002 1.0002 0 00-1-1H4z"/></svg>
        </button>
        <button type="button" v-clipboard:copy="template2">
          Copy Html 
          <svg class="inline-block h-4 w-4 m-2 fill-current" viewBox="0 0 24 24"><path d="M11.553 1.106a1 1 0 01.894 0l10 5a1 1 0 010 1.788l-10 5a1 1 0 01-.894 0l-10-5a1 1 0 010-1.788l10-5zM4.236 7L12 10.882 19.764 7 12 3.118 4.236 7zM1.106 16.553a1 1 0 011.341-.447L12 20.882l9.553-4.776a1 1 0 11.894 1.788l-10 5a1 1 0 01-.894 0l-10-5a1 1 0 01-.447-1.341z"/><path d="M1.106 11.553a1 1 0 011.341-.447L12 15.882l9.553-4.776a1 1 0 11.894 1.788l-10 5a1 1 0 01-.894 0l-10-5a1 1 0 01-.447-1.341z"/></svg>
        </button>
      </div>
    </div>
</div>
</template>

<script>
import Header from '@/components/Header.vue';
export default {
  components:{
    Header
  },
  data(){
    return{
      img_url:'https://signature-gen.netlify.app/smit-patel.jpeg',
      name:'Smit Patel',
      company_name: 'SMITPATELX',
      position:'Full Stack Engineer',
      email:'smitpatel.dev@gmail.com',
      phone:'0000000000',
      website:'smitpatelx.com',
      linkedin_url:'https://www.linkedin.com/in/smitpatelx/',
      instagram_url:'https://www.instagram.com/smit.dev/',
      facebook_url: 'https://www.facebook.com/smitpatelx/',
      twitter_url:'https://twitter.com/smitpatelx',
      banner_url_target: 'http://smitpatelx.com/',
      banner_url: '/banner.png',
    }
  },
  methods:{
    formate_phone(val){
      let phone = val.split('');
      phone.splice(0, 0, "+1-");
      phone.splice(4, 0, "-");
      phone.splice(8, 0, "-");
      return phone.join('');
    },
    copy(){
      var range = document.createRange();
      range.selectNode(document.getElementById("signature"));
      window.getSelection().removeAllRanges(); // clear current selection
      window.getSelection().addRange(range); // to select text
      document.execCommand("copy");
      window.getSelection().removeAllRanges();
    },
    copy2(){
      var range = document.createRange();
      range.selectNode(document.getElementById("signature2"));
      window.getSelection().removeAllRanges(); // clear current selection
      window.getSelection().addRange(range); // to select text
      document.execCommand("copy");
      window.getSelection().removeAllRanges();
    }
  },
  computed:{
    template(){
      let text = `<table id="signature" style="max-width: 600px; direction: ltr;background:#fff; border: 4px solid #fff;"> <tbody class=""> <tr class=""> <td class=""> <table class="html new_10 wisestamp_app main_sig" border="0" cellpadding="0" cellspacing="0" style="width: 520px; padding-bottom: 15px; margin-bottom: 8px;"> <tbody class=""> <tr class=""> <td valign="top" width="10" style="vertical-align: top; width: 15px;" class=""><img src="${this.img_url}`;
      text += `" alt="photo" width="65" height="65" style="border-top-left-radius: 50%; border-top-right-radius: 50%; border-bottom-right-radius: 50%; border-bottom-left-radius: 50%; max-width: 120px;"></td><td valign="top" style="vertical-align: top; padding-left: 20px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="width: 435px;" class=""> <tbody class=""> <tr class=""> <td style="padding-bottom: 6px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td class=""> <div style="color: rgb(2, 2, 2); padding-bottom: 2px; margin: 0px; font-size: 20px; font-weight: bold; line-height: 18px;" class="">${this.name}`;
      text += `</div><span style="color: rgb(51, 51, 51); font-size: 14px;" class="">${this.position}</span><span style="color: rgb(51, 51, 51); font-size: 14px; font-weight: bold;" class="">, ${this.company_name}`;
      text += `</span> </td></tr></tbody> </table> </td></tr><tr class=""> <td width="328" style="padding-bottom: 7px; padding-top: 5px; width: 328px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" style="margin-top:4px;" width="15px" src="https://signature-gen.netlify.com/phone.png"></td><td style="padding:0 0 0 5px; margin-left: 0px;" class=""><a href="tel:+1${this.phone}" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px; margin: 0px;" class="">${this.formate_phone(this.phone)}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" style="margin-top:4px;" width="15px" src="https://signature-gen.netlify.com/mail.png"></td><td style="padding:0 0 0 5px; margin-left: 0px;" class=""><a href="mailto:${this.email}" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px; margin: 0px;" class="">${this.email}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" style="margin-top:4px;" width="15px" src="https://signature-gen.netlify.com/layout.png"></td><td style="padding:0 0 0 5px; margin-left: 0px;" class=""><a href="http://${this.website}/" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px; margin: 0px;" class="">${this.website}`;
      text += `&nbsp;</a></td></tr></tbody> </table> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr class=""> <td style="padding-top: 15px;" class=""> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr style="padding-top: 15px;" class=""> <td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.linkedin_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/linkedin.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.instagram_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/instagram.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.twitter_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/twitter.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.facebook_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/facebook.png" class=""></a></td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody> </table> <div style="clear: both; height: 0px !important;" class=""></div><table cellpadding="0" cellspacing="0" border="0" class=""> <tbody class=""> <tr class=""> <td class=""> <table class="banner wisestamp_app" style="margin: 8px 8px 0px 0px; display: inline-block;"> <tbody class=""> <tr class=""> <td class=""><a href="${this.banner_url_target}" target="_blank" class=""><img src="${this.banner_url}`;
      text += `" width="75%" style="width: 390px;" class=""></a></td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody></table>`;
      return text;
    },
    template2(){
      let text = `<table id="signature2" style="max-width: 600px; direction: ltr; background: #333; border: 4px solid #333;"> <tbody class=""> <tr class=""> <td class=""> <table class="html new_10 wisestamp_app main_sig" border="0" cellpadding="0" cellspacing="0" style="width: 520px; margin-bottom: 8px;"> <tbody class=""> <tr class=""> <td valign="top" width="10" style="vertical-align: top; width: 15px;" class=""><img src="${this.img_url}`;
      text += `" alt="photo" width="65" height="65" style="border-top-left-radius: 50%; border-top-right-radius: 50%; border-bottom-right-radius: 50%; border-bottom-left-radius: 50%; max-width: 120px;" class=""></td><td valign="top" style="vertical-align: top; padding-left: 20px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="width: 435px;" class=""> <tbody class=""> <tr class=""> <td style="padding-bottom: 6px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td class=""> <div style="color: #fff; padding-bottom: 2px; margin: 0px; font-size: 20px; font-weight: bold; line-height: 18px;" class="">${this.name}`;
      text += `</div><span style="color: #fff; font-size: 14px;" class="">${this.position}</span><span style="color: #fff; font-size: 14px; font-weight: bold;" class="">, ${this.company_name}`;
      text += `</span> </td></tr></tbody> </table> </td></tr><tr class=""> <td width="328" style="padding-bottom: 7px; padding-top: 5px; width: 328px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" style="margin-top:4px;" width="15px" src="https://signature-gen.netlify.com/phone-w.png" class=""></td><td style="padding:0 0 0 5px;" class=""><a href="tel:+1${this.phone}" style="vertical-align: middle; text-decoration: none; color: #fff; font-size: 14px; margin: 0px;" class="">${this.formate_phone(this.phone)}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" style="margin-top:4px;" width="15px" src="https://signature-gen.netlify.com/mail-w.png"></td><td style="padding:0 0 0 5px; margin-left: 0px;" class=""><a href="mailto:${this.email}" style="vertical-align: middle; text-decoration: none; color: #fff; font-size: 14px; margin: 0px;" class="">${this.email}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" style="margin-top:4px;" width="15px" src="https://signature-gen.netlify.com/layout-w.png"></td><td style="padding:0 0 0 5px; margin-left: 0px;" class=""><a href="http://${this.website}/" style="vertical-align: middle; text-decoration: none; color: #fff; font-size: 14px; margin: 0px;" class="">${this.website}`;
      text += `&nbsp;</a></td></tr></tbody> </table> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr class=""> <td style="padding-top: 15px;" class=""> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr style="padding-top: 15px;" class=""> <td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.linkedin_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/linkedin.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.instagram_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/instagram.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.twitter_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/twitter.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.facebook_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/facebook.png" class=""></a></td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody> </table> <div style="clear: both; height: 0px !important;" class=""></div><table cellpadding="0" cellspacing="0" border="0" class=""> <tbody class=""> <tr class=""> <td class=""> <table class="banner wisestamp_app" style="margin: 8px 8px 0px 0px; display: inline-block;"> <tbody class=""> <tr class=""> <td class=""><a href="${this.banner_url_target}" target="_blank" class=""><img src="${this.banner_url}`;
      text += `" width="75%" style="width: 390px;" class=""></a></td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody></table>`;
      return text;
    }
  }
}
</script>

<style lang="scss">
.style-inputs{
  label {
    @apply text-xs font-medium text-gray-600;
  }

  input {
    &:focus{
      outline: none;
    }

    @apply focus:ring focus:ring-teal-200 shadow;
  }

  button {
    &:focus{
      outline: none;
    }

    @apply px-5 py-2 my-1 text-lg font-semibold rounded 
      text-gray-600 hover:text-gray-100 focus:text-gray-100 
      bg-teal-400 hover:bg-teal-600 focus:bg-teal-600  
      transition-all duration-300 shadow-md
      focus:ring focus:ring-teal-200;
  }
}
</style>
