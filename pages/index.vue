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
          <input type="tel" id="phone" v-model="phone" class="w-full text-blue-800 mt-1 px-3 py-1 text-base rounded">
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
      <div class="w-full bg-white py-5 px-3 rounded scrolling-touch overflow-x-scroll" v-html="template" />
      <div class="w-full mt-8 pr-8 flex flex-wrap justify-between">
        <button type="button" v-clipboard:copy="template" class="px-5 py-2 text-lg rounded text-white bg-blue-800 hover:bg-blue-700 shadow-lg transition-all duration-500">
          Copy
          <svg class="inline-block h-4 w-4 ml-3 text-white fill-current" viewBox="0 0 24 24"><path fill-rule="evenodd" clip-rule="evenodd" d="M11 10c-.5523 0-1 .4477-1 1v9c0 .5523.4477 1 1 1h9c.5523 0 1-.4477 1-1v-9c0-.5523-.4477-1-1-1h-9zm-3 1c0-1.6569 1.3431-3 3-3h9c1.6569 0 3 1.3431 3 3v9c0 1.6569-1.3431 3-3 3h-9c-1.6569 0-3-1.3431-3-3v-9z" /><path fill-rule="evenodd" clip-rule="evenodd" d="M4 3a1 1 0 00-1 1v9a1 1 0 001 1h1c.5523 0 1 .4477 1 1s-.4477 1-1 1H4a3 3 0 01-3-3V4a3 3 0 013-3h9a3 3 0 013 3v1c0 .5523-.4477 1-1 1s-1-.4477-1-1V4a1.0002 1.0002 0 00-1-1H4z"/></svg>
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
      company_name: 'Blabbly',
      position:'Director of Web Development',
      email:'smit@blabbly.com',
      phone:'4313388432',
      website:'smitpatelx.com',
      linkedin_url:'https://www.linkedin.com/in/smitpatelx/',
      instagram_url:'https://www.instagram.com/smit.dev/',
      facebook_url: 'https://www.facebook.com/getblabbly/',
      twitter_url:'https://twitter.com/smitpatelx',
      banner_url_target: 'http://blabbly.com/',
      banner_url: 'https://blabbly.com/wp-content/uploads/2020/01/end2.jpg',
      template_1:'<table class="main_html date__2020_02_27___15_50" style="max-width: 600px; direction: ltr;"> <tbody class=""> <tr class=""> <td class=""> <table class="html new_10 wisestamp_app main_sig" border="0" cellpadding="0" cellspacing="0" style="width: 520px; padding-bottom: 15px; margin-bottom: 8px;"> <tbody class=""> <tr class=""> <td valign="top" width="10" style="vertical-align: top; width: 15px;" class=""><img src="https://smitpatelx.com/smit-3.jpg" alt="photo" width="65" height="65" style="border-top-left-radius: 50%; border-top-right-radius: 50%; border-bottom-right-radius: 50%; border-bottom-left-radius: 50%; max-width: 120px;" class=""></td> <td valign="top" style="vertical-align: top; padding-left: 20px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="width: 435px;" class=""> <tbody class=""> <tr class=""> <td style="padding-bottom: 6px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td class=""> <div style="color: rgb(2, 2, 2); padding-bottom: 2px; margin: 0px; font-size: 20px; font-weight: bold; line-height: 18px;" class="">Smit Patel</div><span style="color: rgb(51, 51, 51); font-size: 14px;" class="">Director of Web Development</span><span style="color: rgb(51, 51, 51); font-size: 14px; font-weight: bold;" class="">, Blabbly</span> </td> </tr> </tbody> </table> </td> </tr> <tr class=""> <td width="328" style="padding-bottom: 7px; padding-top: 5px; width: 328px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td style="padding-right: 15px; width: 15px; padding-bottom: 3px; vertical-align: top;" class=""><img src="https://d1n2mpfyq0bf3x.cloudfront.net/7c730cd01a3a3804b74371fee221c457/phone-icon.png" class=""></td> <td style="padding-bottom: 3px;" class=""><a href="tel:+14313388432" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px;" class="">+1 431-338-8432&nbsp;</a></td> </tr> <tr class=""> <td style="padding-right: 15px; width: 15px; padding-bottom: 3px;" class=""><img src="https://d1n2mpfyq0bf3x.cloudfront.net/7c730cd01a3a3804b74371fee221c457/email-icon.png" class=""></td> <td style="padding-bottom: 3px;" class=""><a href="mailto:smit@blabbly.com" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px;" class="">smit@blabbly.com&nbsp;</a></td> </tr> <tr class=""> <td style="padding-right: 15px; width: 15px; padding-bottom: 3px;" class=""><img src="https://d1n2mpfyq0bf3x.cloudfront.net/7c730cd01a3a3804b74371fee221c457/browser.png" class=""></td> <td style="padding-bottom: 3px;" class=""><a href="http://blabbly.com/" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px;" class="">blabbly.com&nbsp;</a></td> </tr> </tbody> </table> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr class=""> <td style="padding-top: 15px;" class=""> <table border="0" cellpadding="0" cellspacing="0" class=""> <tbody class=""> <tr style="padding-top: 15px;" class=""> <td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="https://www.linkedin.com/in/smitpatelx/" target="_blank" class=""><img height="30" width="30" src="https://blabbly.com/wp-content/uploads/2020/07/iconfinder_linkedin_circle_black_107159.png" class=""></a></td> <td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="http://instagram.com/smit.dev" target="_blank" class=""><img height="30" width="30" src="https://blabbly.com/wp-content/uploads/2020/07/iconfinder_78-instagram_104425.png" class=""></a></td> <td align="left" style="padding-right: 5px; text-align: center; padding-top: 0px;" class=""><a href="https://twitter.com/smitpatelx" target="_blank" class=""><img height="30" width="30" src="https://blabbly.com/wp-content/uploads/2020/07/iconfinder_twitter_circle_black_107155.png" class=""></a></td> </tr> </tbody> </table> </td> </tr> </tbody> </table> </td> </tr> </tbody> </table> </td> </tr> </tbody> </table> <div style="clear: both; height: 0px !important;" class=""></div> <table cellpadding="0" cellspacing="0" border="0" class=""> <tbody class=""> <tr class=""> <td class=""> <table class="banner wisestamp_app" style="margin: 8px 8px 0px 0px; display: inline-block;"> <tbody class=""> <tr class=""> <td class=""><a href="http://blabbly.com" target="_blank" class=""><img src="https://blabbly.com/wp-content/uploads/2020/01/end2.jpg" width="75%" style="width: 390px;" class=""></a></td> </tr> </tbody> </table> </td> </tr> </tbody> </table> </td> </tr> </tbody></table>'
    }
  },
  methods:{
    formate_phone(val){
      let phone = val.split('');
      phone.splice(4, 0, "-");
      phone.splice(8, 0, "-");
      return phone.join('');
    },
    copy(){

    }
  },
  computed:{
    template(){
      let text = `<table class="main_html date__2020_02_27___15_50" style="max-width: 600px; direction: ltr;"> <tbody class=""> <tr class=""> <td class=""> <table class="html new_10 wisestamp_app main_sig" border="0" cellpadding="0" cellspacing="0" style="width: 520px; padding-bottom: 15px; margin-bottom: 8px;"> <tbody class=""> <tr class=""> <td valign="top" width="10" style="vertical-align: top; width: 15px;" class=""><img src="${this.img_url}`;
      text += `" alt="photo" width="65" height="65" style="border-top-left-radius: 50%; border-top-right-radius: 50%; border-bottom-right-radius: 50%; border-bottom-left-radius: 50%; max-width: 120px;" class=""></td><td valign="top" style="vertical-align: top; padding-left: 20px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="width: 435px;" class=""> <tbody class=""> <tr class=""> <td style="padding-bottom: 6px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td class=""> <div style="color: rgb(2, 2, 2); padding-bottom: 2px; margin: 0px; font-size: 20px; font-weight: bold; line-height: 18px;" class="">${this.name}`;
      text += `</div><span style="color: rgb(51, 51, 51); font-size: 14px;" class="">Director of Web Development</span><span style="color: rgb(51, 51, 51); font-size: 14px; font-weight: bold;" class="">, ${this.company_name}`;
      text += `</span> </td></tr></tbody> </table> </td></tr><tr class=""> <td width="328" style="padding-bottom: 7px; padding-top: 5px; width: 328px;" class=""> <table border="0" cellpadding="0" cellspacing="0" width="100%" style="line-height: 1.6; font-family: Arial; font-size: 11px; color: rgb(78, 75, 76); padding-left: 2px; width: 433px;" class=""> <tbody class=""> <tr class=""> <td style="padding-right: 15px; width: 15px; padding-bottom: 3px; vertical-align: top;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/phone.png" class=""></td><td style="padding-bottom: 3px;" class=""><a href="tel:+1${this.phone}" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px;" class="">${this.formate_phone(this.phone)}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 15px; width: 15px; padding-bottom: 3px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/mail.png" class=""></td><td style="padding-bottom: 3px;" class=""><a href="mailto:${this.email}" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px;" class="">${this.email}`;
      text += `&nbsp;</a></td></tr><tr class=""> <td style="padding-right: 15px; width: 15px; padding-bottom: 3px;" class=""><img height="15px" width="15px" src="https://signature-gen.netlify.com/layout.png" class=""></td><td style="padding-bottom: 3px;" class=""><a href="http://${this.website}/" style="vertical-align: middle; text-decoration: none; color: rgb(51, 51, 51); font-size: 14px;" class="">${this.website}`;
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
