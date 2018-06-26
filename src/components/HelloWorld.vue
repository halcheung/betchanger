<template>
  <div class="hello">
    <table style="width:600px;">
      <thead>
        <tr>
          <th colspan="3">独赢</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>{{teamA}}<b>{{singlePayA}}</b></td>
          <td>{{equal}}<b>{{singlePayE}}</b></td>
          <td>{{teamB}}<b>{{singlePayB}}</b></td>
        </tr>
      </tbody>
    </table>
    <table style="width:600px;" v-show="hasFirstHalf">
      <thead>
        <tr>
          <th colspan="3">独赢 <span style="color:#ffd796;font-family:Arial,'宋体';">- 上半场</span></th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>{{teamA}}<b>{{singlePayA2}}</b></td>
          <td>{{equal}}<b>{{singlePayE2}}</b></td>
          <td>{{teamB}}<b>{{singlePayB2}}</b></td>
        </tr>
      </tbody>
    </table>
    <table style="width:600px;">
      <thead>
        <tr>
          <th colspan="5">波胆</th>
        </tr>
      </thead>
      <tbody class="score">
        <tr class="subhead">
          <td colspan="2">{{teamA}}</td>
          <td>{{equal}}</td>
          <td colspan="2">{{teamB}}</td>
        </tr>
        <tr v-for="scr in scores">
          <td v-for="ss in scr">{{ss.s}}<b>{{ss.b}}</b></td>
        </tr>
        <tr>
          <td colspan="5"><span class="other">其它比分</span><b>{{otherscore}}</b></td>
        </tr>
      </tbody>
    </table>
    <table style="width:600px;" v-show="hasFirstHalf">
      <thead>
      <tr>
        <th colspan="5">波胆 <span style="color:#ffd796;font-family:Arial,'宋体';">- 上半场</span></th>
      </tr>
      </thead>
      <tbody class="score">
      <tr class="subhead">
        <td colspan="2">{{teamA}}</td>
        <td>{{equal}}</td>
        <td colspan="2">{{teamB}}</td>
      </tr>
      <tr v-for="scr in scores2">
        <td v-for="ss in scr">{{ss.s}}<b>{{ss.b}}</b></td>
      </tr>
      <tr>
        <td colspan="5"><span class="other">其它比分</span><b>{{otherscore2}}</b></td>
      </tr>
      </tbody>
    </table>

    <table style="width:600px;">
      <thead>
      <tr>
        <th>&nbsp;</th>
      </tr>
      </thead>
    </table>

    <div class="right-border">
      <table style="width:250px;margin-top:10px;">
        <thead>
        <tr>
          <th>独赢</th>
        </tr>
        </thead>
        <tbody>
        <tr>
          <td style="font-size:14px;"><input type="text" v-model="ms[1]" @input="input" />&nbsp;
            <input type="radio" name="a" id="a1" value="1" v-model="multiple1" /><label for="a1">乘以(×)</label>
            <input type="radio" name="a" id="a2" value="2" v-model="multiple1" /><label for="a2">减去(-)</label>
          </td>
        </tr>
        </tbody>
      </table>
      <table style="width:250px;">
        <thead>
        <tr>
          <th>独赢 <span style="color:#ffd796;font-family:Arial,'宋体';">- 上半场</span></th>
        </tr>
        </thead>
        <tbody>
        <tr>
          <td style="font-size:14px;"><input type="text" v-model="ms[2]" @input="input" />&nbsp;
            <input type="radio" name="b" id="b1" value="1" v-model="multiple2"/><label for="b1">乘以(×)</label>
            <input type="radio" name="b" id="b2" value="2" v-model="multiple2" /><label for="b2">减去(-)</label></td>
        </tr>
        </tbody>
      </table>
      <table style="width:250px;">
        <thead>
        <tr>
          <th>波胆</th>
        </tr>
        </thead>
        <tbody class="score">
        <tr class="subhead">
          <td style="padding:8px 0;">&nbsp;</td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[3]" @input="input" /> &nbsp;
            <input type="radio" name="c" id="c1" value="1" v-model="multiple3" /><label for="c1">乘以(×)</label>
            <input type="radio" name="c" id="c2" value="2" v-model="multiple3" /><label for="c2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[4]" @input="input" /> &nbsp;
            <input type="radio" name="d" id="d1" value="1" v-model="multiple4"/><label for="d1">乘以(×)</label>
            <input type="radio" name="d" id="d2" value="2" v-model="multiple4" /><label for="d2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[5]" @input="input" /> &nbsp;
            <input type="radio" name="e" id="e1" value="1" v-model="multiple5"/><label for="e1">乘以(×)</label>
            <input type="radio" name="e" id="e2" value="2" v-model="multiple5" /><label for="e2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[6]" @input="input" /> &nbsp;
            <input type="radio" name="f" id="f1" value="1" v-model="multiple6"/><label for="f1">乘以(×)</label>
            <input type="radio" name="f" id="f2" value="2" v-model="multiple6" /><label for="f2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[7]" @input="input" /> &nbsp;
            <input type="radio" name="g" id="g1" value="1" v-model="multiple7"/><label for="g1">乘以(×)</label>
            <input type="radio" name="g" id="g2" value="2" v-model="multiple7" /><label for="g2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[8]" @input="input" /> &nbsp;
            <input type="radio" name="h" id="h1" value="1" v-model="multiple8"/><label for="h1">乘以(×)</label>
            <input type="radio" name="h" id="h2" value="2" v-model="multiple8" /><label for="h2">减去(-)</label></td>
        </tr>
        </tbody>
      </table>
      <table style="width:250px;">
        <thead>
        <tr>
          <th>波胆 <span style="color:#ffd796;font-family:Arial,'宋体';">- 上半场</span></th>
        </tr>
        </thead>
        <tbody class="score">
        <tr class="subhead">
          <td style="padding:8px 0;">&nbsp;</td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[9]" @input="input" /> &nbsp;
            <input type="radio" name="i" id="i1" value="1" v-model="multiple9"/><label for="i1">乘以(×)</label>
            <input type="radio" name="i" id="i2" value="2" v-model="multiple9" /><label for="i2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[10]" @input="input" /> &nbsp;
            <input type="radio" name="j" id="j1" value="1" v-model="multiple10"/><label for="j1">乘以(×)</label>
            <input type="radio" name="j" id="j2" value="2" v-model="multiple10" /><label for="j2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[11]" @input="input" /> &nbsp;
            <input type="radio" name="k" id="k1" value="1" v-model="multiple11"/><label for="k1">乘以(×)</label>
            <input type="radio" name="k" id="k2" value="2" v-model="multiple11" /><label for="k2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[12]" @input="input" /> &nbsp;
            <input type="radio" name="l" id="l1" value="1" v-model="multiple12"/><label for="l1">乘以(×)</label>
            <input type="radio" name="l" id="l2" value="2" v-model="multiple12" /><label for="l2">减去(-)</label></td>
        </tr>
        <tr>
          <td><input type="text" v-model="ms[13]" @input="input" /> &nbsp;
            <input type="radio" name="m" id="m1" value="1" v-model="multiple13"/><label for="m1">乘以(×)</label>
            <input type="radio" name="m" id="m2" value="2" v-model="multiple13" /><label for="m2">减去(-)</label></td>
        </tr>
        </tbody>
      </table>

      <p style="background-color:#f2f2f2;padding:10px;">全部：
        <input type="radio" name="all" id="all1" value="1" v-model="multipleall"/><label for="all1">乘以(×)</label>
        <input type="radio" name="all" id="all2" value="2" v-model="multipleall" /><label for="all2">减去(-)</label>
      </p>

      <button type="button" style="font-size:12px;width:100px;text-align:center;padding:10px;margin-top:10px;" @click="apply">应用</button> &nbsp;
      <button type="button" style="font-size:12px;width:100px;text-align:center;padding:10px;margin-top:10px;" @click="reset">重置</button>

    </div>

    <textarea style="margin-top:10px;border:solid 2px #000;" cols="81" rows="16" v-model="html"></textarea>
    <p>
      <button type="button" style="font-size:12px;width:100px;text-align:center;padding:10px;" @click="recognize">导入</button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      hasFirstHalf:true,
      teamA: '主队',
      teamB: '客队',
      equal: '和局',
      scores: [
        [
          {s:'9 - 9', b: '1.0'},
          {s:'9 - 9', b: '1.0'},
          {s:'9 - 9', b: '1.0'},
          {s:'9 - 9', b: '1.0'},
          {s:'9 - 9', b: '1.0'},
        ]
      ],
      scores2: [
        [
          {s:'8 - 8', b: '1.0'},
          {s:'8 - 8', b: '1.0'},
          {s:'8 - 8', b: '1.0'},
          {s:'8 - 8', b: '1.0'},
          {s:'8 - 8', b: '1.0'},
        ]
      ],
      ms: [1,1,1,1,1,1,1,1,1,1,1,1,1,1],
      otherscore: '0.0',
      otherscore2: '0.0',
      html: '',
      singlePayA: 0,
      singlePayE: 0,
      singlePayB: 0,
      singlePayA2: 0,
      singlePayE2: 0,
      singlePayB2: 0,
      multiple1: '1',
      multiple2: '1',
      multiple3: '1',
      multiple4: '1',
      multiple5: '1',
      multiple6: '1',
      multiple7: '1',
      multiple8: '1',
      multiple9: '1',
      multiple10: '1',
      multiple11: '1',
      multiple12: '1',
      multiple13: '1',
      multipleall: '1',
    }
  },
  methods:{
    reset(){
      this.ms = [1,1,1,1,1,1,1,1,1,1,1,1,1,1];
      this.multipleall = '2';
      setTimeout(this.resetMultiple,0);
    },
    resetMultiple(){
      this.multipleall = '1';
    },
    input(event){
      let val = event.target.value.trim();
      if(val.indexOf('.') == val.length - 1) return;
      this.changeBet();
    },
    apply(){
      this.recognize();
      for(let i=0;i<this.ms.length;i++){
        if(i==1){
          if(this.multiple1 == '1') {
            this.singlePayA = this.singlePayA == '-' ? '-' : (this.singlePayA * this.ms[i]).toFixed(2);
            this.singlePayE = this.singlePayE == '-' ? '-' : (this.singlePayE * this.ms[i]).toFixed(2);
            this.singlePayB = this.singlePayB == '-' ? '-' : (this.singlePayB * this.ms[i]).toFixed(2);
          } else {
            this.singlePayA = this.singlePayA == '-' ? '-' : (this.singlePayA - this.ms[i]).toFixed(2);
            this.singlePayE = this.singlePayE == '-' ? '-' : (this.singlePayE - this.ms[i]).toFixed(2);
            this.singlePayB = this.singlePayB == '-' ? '-' : (this.singlePayB - this.ms[i]).toFixed(2);
          }
        }
        if(i==2){
          if(this.multiple2 == '1') {
            this.singlePayA2 = this.singlePayA2 == '-' ? '-' : (this.singlePayA2 * this.ms[i]).toFixed(2);
            this.singlePayE2 = this.singlePayE2 == '-' ? '-' : (this.singlePayE2 * this.ms[i]).toFixed(2);
            this.singlePayB2 = this.singlePayB2 == '-' ? '-' : (this.singlePayB2 * this.ms[i]).toFixed(2);
          } else {
            this.singlePayA2 = this.singlePayA2 == '-' ? '-' : (this.singlePayA2 - this.ms[i]).toFixed(2);
            this.singlePayE2 = this.singlePayE2 == '-' ? '-' : (this.singlePayE2 - this.ms[i]).toFixed(2);
            this.singlePayB2 = this.singlePayB2 == '-' ? '-' : (this.singlePayB2 - this.ms[i]).toFixed(2);
          }
        }
        if(i>=3 && i<=7){
          if(this['multiple'+i] == '1') {
            this.scores[i-3][0].b = this.scores[i-3][0].b == '-' ? '-' : (this.scores[i-3][0].b * this.ms[i]).toFixed(2);
            this.scores[i-3][1].b = this.scores[i-3][1].b == '-' ? '-' : (this.scores[i-3][1].b * this.ms[i]).toFixed(2);
            this.scores[i-3][2].b = this.scores[i-3][2].b == '-' ? '-' : (this.scores[i-3][2].b * this.ms[i]).toFixed(2);
            this.scores[i-3][3].b = this.scores[i-3][3].b == '-' ? '-' : (this.scores[i-3][3].b * this.ms[i]).toFixed(2);
            this.scores[i-3][4].b = this.scores[i-3][4].b == '-' ? '-' : (this.scores[i-3][4].b * this.ms[i]).toFixed(2);
          } else {
            this.scores[i-3][0].b = this.scores[i-3][0].b == '-' ? '-' : (this.scores[i-3][0].b - this.ms[i]).toFixed(2);
            this.scores[i-3][1].b = this.scores[i-3][1].b == '-' ? '-' : (this.scores[i-3][1].b - this.ms[i]).toFixed(2);
            this.scores[i-3][2].b = this.scores[i-3][2].b == '-' ? '-' : (this.scores[i-3][2].b - this.ms[i]).toFixed(2);
            this.scores[i-3][3].b = this.scores[i-3][3].b == '-' ? '-' : (this.scores[i-3][3].b - this.ms[i]).toFixed(2);
            this.scores[i-3][4].b = this.scores[i-3][4].b == '-' ? '-' : (this.scores[i-3][4].b - this.ms[i]).toFixed(2);
          }
        }
        if(i==8){
          if(this['multiple'+i] == '1'){
            this.otherscore = this.otherscore == '-' ? '-' : (this.otherscore * this.ms[i]).toFixed(2);
          } else {
            this.otherscore = this.otherscore == '-' ? '-' : (this.otherscore - this.ms[i]).toFixed(2);
          }
        }
        if(i>=9 && i<=12){
          if(this['multiple'+i] == '1') {
            this.scores2[i-9][0].b = (this.scores2[i-9][0].b == '-' || !this.scores2[i-9][0].b) ? this.scores2[i-9][0].b : (this.scores2[i-9][0].b * this.ms[i]).toFixed(2);
            this.scores2[i-9][1].b = (this.scores2[i-9][1].b == '-' || !this.scores2[i-9][1].b) ? this.scores2[i-9][1].b : (this.scores2[i-9][1].b * this.ms[i]).toFixed(2);
            this.scores2[i-9][2].b = (this.scores2[i-9][2].b == '-' || !this.scores2[i-9][2].b) ? this.scores2[i-9][2].b : (this.scores2[i-9][2].b * this.ms[i]).toFixed(2);
            this.scores2[i-9][3].b = (this.scores2[i-9][3].b == '-' || !this.scores2[i-9][3].b) ? this.scores2[i-9][3].b : (this.scores2[i-9][3].b * this.ms[i]).toFixed(2);
            this.scores2[i-9][4].b = (this.scores2[i-9][4].b == '-' || !this.scores2[i-9][4].b) ? this.scores2[i-9][4].b : (this.scores2[i-9][4].b * this.ms[i]).toFixed(2);
          } else {
            this.scores2[i-9][0].b = (this.scores2[i-9][0].b == '-' || !this.scores2[i-9][0].b) ? this.scores2[i-9][0].b : (this.scores2[i-9][0].b - this.ms[i]).toFixed(2);
            this.scores2[i-9][1].b = (this.scores2[i-9][1].b == '-' || !this.scores2[i-9][1].b) ? this.scores2[i-9][1].b : (this.scores2[i-9][1].b - this.ms[i]).toFixed(2);
            this.scores2[i-9][2].b = (this.scores2[i-9][2].b == '-' || !this.scores2[i-9][2].b) ? this.scores2[i-9][2].b : (this.scores2[i-9][2].b - this.ms[i]).toFixed(2);
            this.scores2[i-9][3].b = (this.scores2[i-9][3].b == '-' || !this.scores2[i-9][3].b) ? this.scores2[i-9][3].b : (this.scores2[i-9][3].b - this.ms[i]).toFixed(2);
            this.scores2[i-9][4].b = (this.scores2[i-9][4].b == '-' || !this.scores2[i-9][4].b) ? this.scores2[i-9][4].b : (this.scores2[i-9][4].b - this.ms[i]).toFixed(2);
          }
        }
        if(i==13){
          if(this['multiple'+i] == '1'){
            this.otherscore2 = this.otherscore2 == '-' ? '-' : (this.otherscore2 * this.ms[i]).toFixed(2);
          } else {
            this.otherscore2 = this.otherscore2 == '-' ? '-' : (this.otherscore2 - this.ms[i]).toFixed(2);
          }
        }
      }
    },
    recognize(){
      if(!this.html){
        return;
      }

      /*
独赢
乌拉圭	1.52
和局	4.10
俄罗斯	6.70
独赢 - 上半场
乌拉圭	1.24
和局	4.60
俄罗斯	18.0
波胆
乌拉圭	和局	俄罗斯
1 - 06.0	2 - 06.0	0 - 0-	0 - 1-	0 - 2-
2 - 16.3	3 - 012.5	1 - 15.6	1 - 210.5	0 - 3-
3 - 114.5	3 - 236	2 - 213.5	1 - 331	2 - 341
4 - 036	4 - 151	3 - 3121	0 - 4-	1 - 4101
4 - 2131	4 - 3351	4 - 4351	2 - 4161	3 - 4351
其他比分51
波胆 - 上半场
乌拉圭	和局	俄罗斯
1 - 01.79	2 - 04.90	0 - 0-	0 - 1-	0 - 2-
2 - 115.0	3 - 031	1 - 14.55	1 - 226	0 - 3-
3 - 186	3 - 2201	2 - 281	1 - 3201	2 - 3201
3 - 3201
其他比分201
      * */

      this.html = this.html.trim();
      this.hasFirstHalf = this.html.indexOf('上半场') != -1;

      let HTML = this.html.split(/\r|\n|\r\n/g);

      this.scores = [];
      this.scores2 = [];
      for(let i=0;i<HTML.length;i++){
        if(HTML[i].indexOf('独赢') != -1 && HTML[i].indexOf('上半场') == -1){
          this.singlePayA = HTML[i+1].split(/\s|\t/g)[1].trim();
          this.singlePayE = HTML[i+2].split(/\s|\t/g)[1].trim();
          this.singlePayB = HTML[i+3].split(/\s|\t/g)[1].trim();
        }
        if(HTML[i].indexOf('独赢') != -1 && HTML[i].indexOf('上半场') != -1){
          this.singlePayA2 = HTML[i+1].split(/\s|\t/g)[1].trim();
          this.singlePayE2 = HTML[i+2].split(/\s|\t/g)[1].trim();
          this.singlePayB2 = HTML[i+3].split(/\s|\t/g)[1].trim();
        }
        if(HTML[i].indexOf('波胆') != -1 && HTML[i].indexOf('上半场') == -1){
          let teams = HTML[i+1];
          this.teamA = teams.split(/\s|\t/g)[0].trim();
          this.teamB = teams.split(/\s|\t/g)[2].trim();
          let lines = [ HTML[i+2], HTML[i+3],HTML[i+4],HTML[i+5],HTML[i+6]];
          for(let j=0;j<lines.length;j++){
            let line = lines[j];
            let cols = line.split(/\t/g);
            let sc = [];
            for(let k=0;k<cols.length;k++){
              sc.push({
                s:cols[k].substr(0,5),
                b:cols[k].substr(5)
              });
            }
            this.scores.push(sc);
          }
          this.scores.concat();
          this.otherscore = HTML[i+7].substr(4).trim();
        }
        if(HTML[i].indexOf('波胆') != -1 && HTML[i].indexOf('上半场') != -1){
          let lines = [ HTML[i+2], HTML[i+3],HTML[i+4]];
          for(let j=0;j<lines.length;j++){
            let line = lines[j];
            let cols = line.split(/\t/g);
            let sc = [];
            for(let k=0;k<cols.length;k++){
              sc.push({
                s:cols[k].substr(0,5),
                b:cols[k].substr(5)
              });
            }
            this.scores2.push(sc);
          }
          let last = HTML[i+5];
          this.scores2.push([
            {s:'',b:''},
            {s:'',b:''},
            {s:last.substr(0,5),b:last.substr(5)},
            {s:'',b:''},
            {s:'',b:''}
          ]);
          this.scores2.concat();
          console.log(HTML[i+6]);
          this.otherscore2 = HTML[i+6].substr(4).trim();
        }
      }
    },
    changeBet(){
      for(let i=0;i<this.ms.length;i++){
        this.ms[i] *= 1;
      }
      this.ms.concat();
      console.log(this.ms);

      this.apply();
    }
  },
  watch:{
    multipleall(){
      this.multiple1 = this.multipleall;
      this.multiple2 = this.multipleall;
      this.multiple3 = this.multipleall;
      this.multiple4 = this.multipleall;
      this.multiple5 = this.multipleall;
      this.multiple6 = this.multipleall;
      this.multiple7 = this.multipleall;
      this.multiple8 = this.multipleall;
      this.multiple9 = this.multipleall;
      this.multiple10 = this.multipleall;
      this.multiple11 = this.multipleall;
      this.multiple12 = this.multipleall;
      this.multiple13 = this.multipleall;
      this.changeBet();
    },
    multiple1(){ this.changeBet(); },
    multiple2(){ this.changeBet(); },
    multiple3(){ this.changeBet(); },
    multiple4(){ this.changeBet(); },
    multiple5(){ this.changeBet(); },
    multiple6(){ this.changeBet(); },
    multiple7(){ this.changeBet(); },
    multiple8(){ this.changeBet(); },
    multiple9(){ this.changeBet(); },
    multiple10(){ this.changeBet(); },
    multiple11(){ this.changeBet(); },
    multiple12(){ this.changeBet(); },
    multiple13(){ this.changeBet(); },
    singlePayA(){
      this.singlePayA = this.singlePayA.substr(-3) == '.00' ? this.singlePayA.substr(0,this.singlePayA.length - 1) : this.singlePayA;
      if(this.singlePayA * 1 > 20 && (this.singlePayA * 1) % 1 == 0){
        this.singlePayA = this.singlePayA.split('.')[0];
      }
      if(this.singlePayA * 1 > 20 && (this.singlePayA * 1) % 1 != 0 && this.singlePayA.substr(-1) == '0'){
        this.singlePayA = (this.singlePayA * 1).toFixed(1);
      }
    },
    singlePayE(){
      this.singlePayE = this.singlePayE.substr(-3) == '.00' ? this.singlePayE.substr(0,this.singlePayE.length - 1) : this.singlePayE;
      if(this.singlePayE * 1 > 20 && (this.singlePayE * 1) % 1 == 0){
        this.singlePayE = this.singlePayE.split('.')[0];
      }
      if(this.singlePayE * 1 > 20 && (this.singlePayE * 1) % 1 != 0 && this.singlePayE.substr(-1) == '0'){
        this.singlePayE = (this.singlePayE * 1).toFixed(1);
      }
    },
    singlePayB(){
      this.singlePayB = this.singlePayB.substr(-3) == '.00' ? this.singlePayB.substr(0,this.singlePayB.length - 1) : this.singlePayB;
      if(this.singlePayB * 1 > 20 && (this.singlePayB * 1) % 1 == 0){
        this.singlePayB = this.singlePayB.split('.')[0];
      }
      if(this.singlePayB * 1 > 20 && (this.singlePayB * 1) % 1 != 0 && this.singlePayB.substr(-1) == '0'){
        this.singlePayB = (this.singlePayB * 1).toFixed(1);
      }
    },
    singlePayA2(){
      this.singlePayA2 = this.singlePayA2.substr(-3) == '.00' ? this.singlePayA2.substr(0,this.singlePayA2.length - 1) : this.singlePayA2;
      if(this.singlePayA2 * 1 > 20 && (this.singlePayA2 * 1) % 1 == 0){
        this.singlePayA2 = this.singlePayA2.split('.')[0];
      }
      if(this.singlePayA2 * 1 > 20 && (this.singlePayA2 * 1) % 1 != 0 && this.singlePayA2.substr(-1) == '0'){
        this.singlePayA2 = (this.singlePayA2 * 1).toFixed(1);
      }
    },
    singlePayE2(){
      this.singlePayE2 = this.singlePayE2.substr(-3) == '.00' ? this.singlePayE2.substr(0,this.singlePayE2.length - 1) : this.singlePayE2;
      if(this.singlePayE2 * 1 > 20 && (this.singlePayE2 * 1) % 1 == 0){
        this.singlePayE2 = this.singlePayE2.split('.')[0];
      }
      if(this.singlePayE2 * 1 > 20 && (this.singlePayE2 * 1) % 1 != 0 && this.singlePayE2.substr(-1) == '0'){
        this.singlePayE2 = (this.singlePayE2 * 1).toFixed(1);
      }
    },
    singlePayB2(){
      this.singlePayB2 = this.singlePayB2.substr(-3) == '.00' ? this.singlePayB2.substr(0,this.singlePayB2.length - 1) : this.singlePayB2;
      if(this.singlePayB2 * 1 > 20 && (this.singlePayB2 * 1) % 1 == 0){
        this.singlePayB2 = this.singlePayB2.split('.')[0];
      }
      if(this.singlePayB2 * 1 > 20 && (this.singlePayB2 * 1) % 1 != 0 && this.singlePayB2.substr(-1) == '0'){
        this.singlePayB2 = (this.singlePayB2 * 1).toFixed(1);
      }
    },
    scores(){
      for(let i=0;i<this.scores.length;i++){
        for(let j=0;j<this.scores[i].length;j++){
          this.scores[i][j].b = this.scores[i][j].b.substr(-3) == '.00' ? this.scores[i][j].b.substr(0,this.scores[i][j].b.length - 1) : this.scores[i][j].b;
          if(this.scores[i][j].b * 1 > 20 && (this.scores[i][j].b * 1) % 1 == 0){
            this.scores[i][j].b = this.scores[i][j].b.split('.')[0];
          }
          if((this.scores[i][j].b * 1) % 1 != 0 && this.scores[i][j].b.substr(-1) == '0'){
            this.scores[i][j].b = (this.scores[i][j].b * 1).toFixed(1);
          }
        }
      }
      this.scores.concat();
    },
    scores2(){
      for(let i=0;i<this.scores2.length;i++){
        for(let j=0;j<this.scores2[i].length;j++){
          this.scores2[i][j].b = this.scores2[i][j].b.substr(-3) == '.00' ? this.scores2[i][j].b.substr(0,this.scores2[i][j].b.length - 1) : this.scores2[i][j].b;
          if(this.scores2[i][j].b * 1 > 20 && (this.scores2[i][j].b * 1) % 1 == 0){
            this.scores2[i][j].b = this.scores2[i][j].b.split('.')[0];
          }
          if((this.scores2[i][j].b * 1) % 1 != 0 && this.scores2[i][j].b.substr(-1) == '0'){
            this.scores2[i][j].b = (this.scores2[i][j].b * 1).toFixed(1);
          }
        }
      }
      this.scores2.concat();
    },
    otherscore(){
        this.otherscore = this.otherscore.substr(-3) == '.00' ? this.otherscore.substr(0,this.otherscore.length - 1) : this.otherscore;
        if(this.otherscore * 1 > 20 && (this.otherscore * 1) % 1 == 0){
          this.otherscore = this.otherscore.split('.')[0];
        }
        if((this.otherscore * 1) % 1 != 0 && this.otherscore.substr(-1) == '0'){
          this.otherscore = (this.otherscore * 1).toFixed(1);
        }
    },
    otherscore2(){
      this.otherscore2 = this.otherscore2.substr(-3) == '.00' ? this.otherscore2.substr(0,this.otherscore2.length - 1) : this.otherscore2;
      if(this.otherscore2 * 1 > 20 && (this.otherscore2 * 1) % 1 == 0){
        this.otherscore2 = this.otherscore2.split('.')[0];
      }
      if((this.otherscore2 * 1) % 1 != 0 && this.otherscore2.substr(-1) == '0'){
        this.otherscore2 = (this.otherscore2 * 1).toFixed(1);
      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  * {
    font-family: '宋体';
    text-align: left;
  }
  table {
    border-spacing:0;
  }
  .right-border {
    position: absolute;
    top:0;
    left:607px;
    height:100%;
    border-right:solid 1px #000;
    border-left:solid 10px #32271e;
    width:300px;
    padding:0 10px;
  }
  thead>tr {
  }
  thead>tr>th {
    background:#6b5444 url(../assets/star.png) no-repeat center right;
    color:#f2dfd2;
    font-size: 14px;
    font-weight:normal;
    padding:7px 9px;
  }
  tbody>tr>td {
    background:#fff;
    color:#000;
    font-size: 12px;
    font-weight:normal;
    padding:9px 12px;
    border:none;
    border-right:solid 1px #baa283;
    border-bottom:solid 1px #efe5d9;
    width:33%;
  }
  tbody>tr>td:last-child {
    border-right:none;
  }
  tbody>tr:last-child>td {
    border-bottom:none;
  }
  tbody>tr>td>b {
    font-family: Arial;
    color:#c8250a;
    display:block;
    float:right;
    font-size:14px;
  }
  tbody.score>tr>td
  {
    font-family: Arial;
    font-size:14px;
    width:20%;
    position: relative;
  }
  tbody.score>tr>td>.other {
    font-family:'宋体';font-size:12px;
    display:block;
    position: absolute;
    top:10px;
    right:71px;
  }
  tbody.score>tr.subhead>td {
    font-family:'宋体';
    background:#cecbb4;color:#5a5a5a;border-color:#cecbb4;font-size:14px;text-align:center;
  }
  .right-border>table>tbody>tr>td{
    padding:1px;
  }
  .right-border>table>tbody>tr>td>input[type=text]{
    padding:5px;
    font-size:16px;
    width:40px;
    text-align:center;
  }
  .right-border>table>tbody>tr>td>input[type=radio] {

  }
</style>
