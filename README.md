# DatepickerTh

## install from git repo สำหรับใช้ภาษาไทย
```bash
npm install leenawat/vuejs-datepicker-th --save
npm install date-fns --save
```
## ตัวอย่างภาษาไทย ปี พ.ศ.
```
<template>
  <div>
    <datepickerTh :language="language" :format="thFormatter" v-model="myDate"></datepickerTh>
  </div>
</template>
<script>

// https://github.com/leenawat/vuejs-datepicker-th
// npm install vuejs-datepicker --save
import DatepickerTh from 'vuejs-datepicker-th'
// locale for datepicker
import { th as datePickerLocalTh } from 'vuejs-datepicker-th/dist/locale'

// https://date-fns.org/
// npm install date-fns --save
import dateFns from 'date-fns'
// locale for dateFns
import dateFnsTh from 'date-fns/locale/th'

export default {
  data () {
    return {
      language: datePickerLocalTh,
      dateFnsLocal: dateFnsTh,
      myDate: new Date()
    }
  },
  components: {
    datepickerTh: DatepickerTh
  },

  methods: {
    thFormatter (date) {
      let yearOffset = 0;
      if (this.selected == 'th') {
        yearOffset = 543;
      }
      return dateFns.format(date, 'D MMM ', { locale: this.dateFnsLocal }) + (parseInt(dateFns.format(date, 'YYYY')) + yearOffset);
    },
  }
}
</script>
```
## ตัวอย่าง 2 ภาษา 
เลือกจาก dropdown เปลี่ยนภาษา และเปลี่ยน ค.ศ. <-> พ.ศ.
```
<template>
  <div>
    <select v-model="selected">
      <option disabled value="">Please select one</option>
      <option value="th" selected>Thai</option>
      <option value="en">English</option>
    </select>
    <datepickerTh :language="language" :format="thFormatter" v-model="myDate"></datepickerTh>
  </div>
</template>
<script>

// https://github.com/leenawat/vuejs-datepicker-th
// npm install vuejs-datepicker --save
import DatepickerTh from 'vuejs-datepicker-th'
// locale for datepicker
import { en as datePickerLocalEn, th as datePickerLocalTh } from 'vuejs-datepicker-th/dist/locale'

// npm install date-fns --save
// https://date-fns.org/
import dateFns from 'date-fns'
// locale for dateFns
import dateFnsTh from 'date-fns/locale/th'
import dateFnsEn from 'date-fns/locale/en'

// สามารถภาษาได้
export default {
  data () {
    return {
      selected: 'th',
      myDate: new Date()
    }
  },
  components: {
    datepickerTh: DatepickerTh
  },
  computed: {
    language () {
      if (this.selected === 'th') {
        return datePickerLocalTh
      } else {
        return datePickerLocalEn
      }
    },
    dateFnsLocal () {
      if (this.selected === 'th') {
        return dateFnsTh
      } else {
        return dateFnsEn
      }

    }
  },

  methods: {
    thFormatter (date) {
      let yearOffset = 0;
      if (this.selected == 'th') {
        yearOffset = 543;
      }
      return dateFns.format(date, 'D MMM ', { locale: this.dateFnsLocal }) + (parseInt(dateFns.format(date, 'YYYY')) + yearOffset);
    },
  }
}
</script>
```
## reference
[https://github.com/charliekassel/vuejs-datepicker](https://github.com/charliekassel/vuejs-datepicker)