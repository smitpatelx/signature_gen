<template>
  <div class="w-full min-h-screen bg-white p-6 flex flex-wrap">
    <Header/>
    <form method="post" @submit.prevent class="w-full md:w-1/2 min-h-screen bg-gray-300 py-6 px-8">
      <h1 class="text-2xl font-semibold">Generate your signature</h1>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="name" class="w-full text-gray-600 text-sm">Full Name</label>
        <input type="text" id="name" v-model="name" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded" required>
      </div>
      <div class="w-full grid grid-cols-2 gap-3 mt-3">
        <div class="w-full flex flex-col">
          <label for="position" class="w-full text-gray-600 text-sm">Position</label>
          <input type="text" id="position" v-model="position" class="w-full text-blue-800 mt-1 px-3 py-1 text-base rounded" required>
        </div>
        <div class="w-full flex flex-col">
          <label for="company_name" class="w-full text-gray-600 text-sm">Company Name</label>
          <input type="text" id="company_name" v-model="company_name" class="w-full text-blue-800 mt-1 px-3 py-1 text-base rounded" required>
        </div>
      </div>
      <div class="w-full grid grid-cols-2 gap-3 mt-3">
        <div class="w-full flex flex-col">
          <label for="email" class="w-full text-gray-600 text-sm">Email</label>
          <input type="email" id="email" v-model="email" class="w-full text-blue-800 mt-1 px-3 py-1 text-base rounded" required>
        </div>
        <div class="w-full flex flex-col">
          <label for="phone" class="w-full text-gray-600 text-sm">Phone</label>
          <div class="flex flex-wrap flex-row justify-start items-stretch mt-1">
            <div class="bg-gray-200 text-gray-700 rounded-l px-3 flex justify-center items-center">+1</div>
            <input type="tel" id="phone" v-model="phone" class="text-blue-800 px-3 py-1 text-base rounded-r flex-1">
          </div>
        </div>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="img_url" class="w-full text-gray-600 text-sm">Image Url</label>
        <input type="url" id="img_url" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded" v-model="img_url" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="website" class="w-full text-gray-600 text-sm">Website</label>
        <input type="url" id="website" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded" v-model="website" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="banner_url" class="w-full text-gray-600 text-sm">Banner</label>
        <input type="url" id="banner_url" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded" v-model="banner_url" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="banner_url_target" class="w-full text-gray-600 text-sm">Banner Url Target</label>
        <input type="url" id="banner_url_target" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded" v-model="banner_url_target" required>
      </div>
      <h2 class="text-2xl font-semibold text-gray-900 mt-4">Social:</h2>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="linkedin" class="w-full text-gray-600 text-sm">Linkedin Url</label>
        <input type="url" id="linkedin" v-model="linkedin_url" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded" required>
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="twitter" class="w-full text-gray-600 text-sm">Twitter Url</label>
        <input type="url" id="twitter" v-model="twitter_url" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded">
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="instagram" class="w-full text-gray-600 text-sm">Instagram Url</label>
        <input type="url" id="instagram" v-model="instagram_url" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded">
      </div>
      <div class="w-full mt-3 pr-8 flex flex-col">
        <label for="facebook" class="w-full text-gray-600 text-sm">Facebook Page Url</label>
        <input type="url" id="facebook" v-model="facebook_url" class="w-full md:w-2/3 text-blue-800 mt-1 px-3 py-1 text-base rounded">
      </div>
      <div class="w-full mt-8 pr-8 flex flex-wrap justify-between">
        <!-- <button type="submit" class="px-5 py-2 text-lg rounded text-white bg-blue-800 hover:bg-blue-700 shadow-lg transition-all duration-500">
          Generate
        </button> -->
        <button type="reset" class="px-5 py-2 text-lg rounded text-blue-800 bg-blue-200 hover:bg-blue-300 shadow-lg  border border-blue-800 transition-all duration-500">
          Reset
        </button>
      </div>
    </form>
    <div class="w-full md:w-1/2 min-h-screen bg-gray-500 py-6 px-8 flex flex-wrap flex-col items-start">
      <h1 class="text-2xl font-semibold text-gray-900 mb-3">Output:</h1>
      <div class="w-full bg-white py-5 px-3 rounded scrolling-touch overflow-x-scroll signature" v-html="template" />
      <div class="w-full mt-8 pr-8 flex flex-wrap justify-between">
        <button type="button" @click="copy()" class="px-5 py-2 text-lg rounded text-white bg-blue-800 hover:bg-blue-700 shadow-lg transition-all duration-500">
          Copy 
          <svg class="inline-block h-4 w-4 ml-3 text-white fill-current" viewBox="0 0 24 24"><path fill-rule="evenodd" clip-rule="evenodd" d="M11 10c-.5523 0-1 .4477-1 1v9c0 .5523.4477 1 1 1h9c.5523 0 1-.4477 1-1v-9c0-.5523-.4477-1-1-1h-9zm-3 1c0-1.6569 1.3431-3 3-3h9c1.6569 0 3 1.3431 3 3v9c0 1.6569-1.3431 3-3 3h-9c-1.6569 0-3-1.3431-3-3v-9z" /><path fill-rule="evenodd" clip-rule="evenodd" d="M4 3a1 1 0 00-1 1v9a1 1 0 001 1h1c.5523 0 1 .4477 1 1s-.4477 1-1 1H4a3 3 0 01-3-3V4a3 3 0 013-3h9a3 3 0 013 3v1c0 .5523-.4477 1-1 1s-1-.4477-1-1V4a1.0002 1.0002 0 00-1-1H4z"/></svg>
        </button>
        <button type="button" v-clipboard:copy="template" class="px-5 py-2 text-lg rounded text-white bg-blue-800 hover:bg-blue-700 shadow-lg transition-all duration-500">
          Copy Html 
          <svg class="inline-block h-5 w-5 ml-2 text-white fill-current" viewBox="0 0 641 512"><path d="M279 511.5l-61-17.7a12 12 0 01-8.3-15L346.2 8.8a12 12 0 0115-8.2l61 17.7a12 12 0 018.1 14.9L293.8 503.3a12 12 0 01-14.9 8.2zM165 399.3l43.4-46.4a12 12 0 00-.8-17.2L117 256l90.6-79.7a12 12 0 00.8-17.2L165 112.7a12 12 0 00-17-.5L4 247.2a12 12 0 000 17.5l144 135a12 12 0 0017-.4zm327.1.6l144.1-135.1a12 12 0 000-17.5L492.2 112a12.1 12.1 0 00-17 .5L431.5 159a12 12 0 00.8 17.2L523 256l-90.6 79.7a12 12 0 00-.8 17.2l43.5 46.4a12 12 0 0017 .6z"/></svg>
        </button>
      </div>

      <h1 class="text-2xl font-semibold text-gray-900 mt-4 mb-3">Dark Version:</h1>
      <div class="w-full bg-white py-5 px-3 rounded scrolling-touch overflow-x-scroll signature" v-html="template2" />
      <div class="w-full mt-8 pr-8 flex flex-wrap justify-between">
        <button type="button" @click="copy2()" class="px-5 py-2 text-lg rounded text-white bg-blue-800 hover:bg-blue-700 shadow-lg transition-all duration-500">
          Copy 
          <svg class="inline-block h-4 w-4 ml-3 text-white fill-current" viewBox="0 0 24 24"><path fill-rule="evenodd" clip-rule="evenodd" d="M11 10c-.5523 0-1 .4477-1 1v9c0 .5523.4477 1 1 1h9c.5523 0 1-.4477 1-1v-9c0-.5523-.4477-1-1-1h-9zm-3 1c0-1.6569 1.3431-3 3-3h9c1.6569 0 3 1.3431 3 3v9c0 1.6569-1.3431 3-3 3h-9c-1.6569 0-3-1.3431-3-3v-9z" /><path fill-rule="evenodd" clip-rule="evenodd" d="M4 3a1 1 0 00-1 1v9a1 1 0 001 1h1c.5523 0 1 .4477 1 1s-.4477 1-1 1H4a3 3 0 01-3-3V4a3 3 0 013-3h9a3 3 0 013 3v1c0 .5523-.4477 1-1 1s-1-.4477-1-1V4a1.0002 1.0002 0 00-1-1H4z"/></svg>
        </button>
        <button type="button" v-clipboard:copy="template2" class="px-5 py-2 text-lg rounded text-white bg-blue-800 hover:bg-blue-700 shadow-lg transition-all duration-500">
          Copy Html 
          <svg class="inline-block h-5 w-5 ml-2 text-white fill-current" viewBox="0 0 641 512"><path d="M279 511.5l-61-17.7a12 12 0 01-8.3-15L346.2 8.8a12 12 0 0115-8.2l61 17.7a12 12 0 018.1 14.9L293.8 503.3a12 12 0 01-14.9 8.2zM165 399.3l43.4-46.4a12 12 0 00-.8-17.2L117 256l90.6-79.7a12 12 0 00.8-17.2L165 112.7a12 12 0 00-17-.5L4 247.2a12 12 0 000 17.5l144 135a12 12 0 0017-.4zm327.1.6l144.1-135.1a12 12 0 000-17.5L492.2 112a12.1 12.1 0 00-17 .5L431.5 159a12 12 0 00.8 17.2L523 256l-90.6 79.7a12 12 0 00-.8 17.2l43.5 46.4a12 12 0 0017 .6z"/></svg>
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
      company_name: 'Netdevv',
      position:'Director of Web Development',
      email:'smitpatel.dev@gmail.com',
      phone:'0000000000',
      website:'blabbly.com',
      linkedin_url:'https://www.linkedin.com/company/blabbly',
      instagram_url:'https://www.instagram.com/getblabbly/',
      facebook_url: 'https://www.facebook.com/getblabbly/',
      twitter_url:'https://twitter.com/getblabbly',
      banner_url_target: 'http://smitpatelx.com/',
      banner_url: 'https://blabbly.com/wp-content/uploads/2020/01/end2.jpg',
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
      let text = `<table id="signature" style="max-width: 600px; direction: ltr;background:#fff; border: 30px solid #fff;"> <tbody class=""> <tr class=""> <td class=""> <table class="html new_10 wisestamp_app main_sig" border="0" cellpadding="0" cellspacing="0" style="width: 520px; padding-bottom: 15px; margin-bottom: 8px;"> <tbody class=""> <tr class=""> <td valign="top" width="10" style="vertical-align: top; width: 15px;" class=""><img src="${this.img_url}`;
      text += `" alt="photo" width="65" height="65" style="border-top-left-radius: 50%; border-top-right-radius: 50%; border-bottom-right-radius: 50%; border-bottom-left-radius: 50%; max-width: 120px;" class=""></td><td valign="top" style="vertical-align: top; padding-left: 20px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="width: 435px;" class=""> <tbody class=""> <tr class=""> <td style="padding-bottom: 6px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td class=""> <div style="color: rgb(2, 2, 2); padding-bottom: 2px; margin: 0px; font-size: 20px; font-weight: bold; line-height: 18px;" class="">${this.name}`;
      text += `</div><span style="color: rgb(51, 51, 51); font-size: 14px;" class="">${this.position}</span><span style="color: rgb(51, 51, 51); font-size: 14px; font-weight: bold;" class="">, ${this.company_name}`;
      text += `</span> </td></tr></tbody> </table> </td></tr><tr class=""> <td width="328" style="padding-bottom: 7px; padding-top: 5px; width: 328px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/phone.png" class=""></td><td style="padding-bottom: 3px; margin-left: 0px;" class=""><a href="tel:+1${this.phone}" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px; margin-left: 10px;" class="">${this.formate_phone(this.phone)}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/mail.png" class=""></td><td style="padding-bottom: 3px; margin-left: 0px;" class=""><a href="mailto:${this.email}" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px; margin-left: 10px;" class="">${this.email}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/layout.png" class=""></td><td style="padding-bottom: 3px; margin-left: 0px;" class=""><a href="http://${this.website}/" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px; margin-left: 10px;" class="">${this.website}`;
      text += `&nbsp;</a></td></tr></tbody> </table> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr class=""> <td style="padding-top: 15px;" class=""> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr style="padding-top: 15px;" class=""> <td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.linkedin_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/linkedin.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.instagram_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/instagram.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.twitter_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/twitter.png" class=""></a></td><td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="${this.facebook_url}`;
      text += `" target="_blank" class=""><img height='30px' width='30px' src="https://signature-gen.netlify.com/socials/facebook.png" class=""></a></td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody> </table> <div style="clear: both; height: 0px !important;" class=""></div><table cellpadding="0" cellspacing="0" border="0" class=""> <tbody class=""> <tr class=""> <td class=""> <table class="banner wisestamp_app" style="margin: 8px 8px 0px 0px; display: inline-block;"> <tbody class=""> <tr class=""> <td class=""><a href="${this.banner_url_target}" target="_blank" class=""><img src="${this.banner_url}`;
      text += `" width="75%" style="width: 390px;" class=""></a></td></tr></tbody> </table> </td></tr></tbody> </table> </td></tr></tbody></table>`;
      return text;
    },
    template2(){
      let text = `<table id="signature2" style="max-width: 600px; direction: ltr; background: #333333; border: 30px solid #333333;"> <tbody class=""> <tr class=""> <td class=""> <table class="html new_10 wisestamp_app main_sig" border="0" cellpadding="0" cellspacing="0" style="width: 520px; margin-bottom: 8px;"> <tbody class=""> <tr class=""> <td valign="top" width="10" style="vertical-align: top; width: 15px;" class=""><img src="${this.img_url}`;
      text += `" alt="photo" width="65" height="65" style="border-top-left-radius: 50%; border-top-right-radius: 50%; border-bottom-right-radius: 50%; border-bottom-left-radius: 50%; max-width: 120px;" class=""></td><td valign="top" style="vertical-align: top; padding-left: 20px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="width: 435px;" class=""> <tbody class=""> <tr class=""> <td style="padding-bottom: 6px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td class=""> <div style="color: #fff; padding-bottom: 2px; margin: 0px; font-size: 20px; font-weight: bold; line-height: 18px;" class="">${this.name}`;
      text += `</div><span style="color: #fff; font-size: 14px;" class="">${this.position}</span><span style="color: #fff; font-size: 14px; font-weight: bold;" class="">, ${this.company_name}`;
      text += `</span> </td></tr></tbody> </table> </td></tr><tr class=""> <td width="328" style="padding-bottom: 7px; padding-top: 5px; width: 328px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/phone-w.png" class=""></td><td style="padding-bottom: 3px;" class=""><a href="tel:+1${this.phone}" style="vertical-align: middle; text-decoration: none; color: #fff; font-size: 14px; margin-left: 10px;" class="">${this.formate_phone(this.phone)}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/mail-w.png" class=""></td><td style="padding-bottom: 3px; margin-left: 0px;" class=""><a href="mailto:${this.email}" style="vertical-align: middle; text-decoration: none; color: #fff; font-size: 14px; margin-left: 10px;" class="">${this.email}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 0px; width: 15px; padding-bottom: 0px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/layout-w.png" class=""></td><td style="padding-bottom: 3px; margin-left: 0px;" class=""><a href="http://${this.website}/" style="vertical-align: middle; text-decoration: none; color: #fff; font-size: 14px; margin-left: 10px;" class="">${this.website}`;
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

<style>

</style>
