<script>

import VueI18n from 'vue-i18n';
import Vue from "vue";

Vue.use(VueI18n);

export default new VueI18n ({
  locale: 'zh-Hans',
  messages: {
    'zh-Hans': require('./lang/zh/zh-Hans'),
    'zh-Hant': require('./lang/zh/zh-Hant'),
    'en-US': require('./lang/en/en-US'),
  }
});

</script>