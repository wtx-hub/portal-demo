<template>
  <div id="addCustomer">
      <el-tabs style="margin-left: 20px;margin-top: 40px">
        <el-tab-pane label="基本信息>>" >
          <span>基本信息</span>
          <el-form :model="allInfo" :rules="rules" ref="ruleForm" label-position="top" style="width:800px;margin-left: 100px;padding-top: 10px" label-width="100px" class="demo-ruleForm" lable="借款人基本信息">
            <el-form-item label="渠道来源" prop="channelSource">
              <el-select v-model="allInfo.channelSource" placeholder="请选择">
                <el-option label="渠道" value="channel"></el-option>
                <el-option label="客户经理" value="Manager"></el-option>
                <el-option label="本人" value="self"></el-option>
                <el-option label="客户转介" value="referral"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="姓名" prop="name">
              <el-input v-model="allInfo.name" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="曾用名" prop="formerName">
              <el-input v-model="allInfo.formerName" placeholder="默认为：无"></el-input>
            </el-form-item>
            <el-form-item label="身份证号" prop="idNumber">
              <el-input v-model="allInfo.idNumber" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="性别" prop="sex">
              <el-select v-model="allInfo.sex" placeholder="请选择">
                <el-option label="男" value="male"></el-option>
                <el-option label="女" value="female"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="手机号" prop="phone">
              <el-input v-model="allInfo.phone" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="学历情况" prop="educational">
              <el-select v-model="allInfo.educational" placeholder="请选择">
                <el-option label="博士研究生毕业" value="doctoral"></el-option>
                <el-option label="硕士研究生毕业" value="master"></el-option>
                <el-option label="大学本科生毕业" value="bachelor"></el-option>
                <el-option label="大学专科生毕业" value="juniorCollege"></el-option>
                <el-option label="中等职业教育" value="vocational"></el-option>
                <el-option label="普通高级中学毕业" value="general"></el-option>
                <el-option label="初级中学教育" value="junior"></el-option>
                <el-option label="小学教育" value="primary"></el-option>
                <el-option label="其他" value="others"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="户籍地址" prop="residenceAddress" >
              <template>
                <v-distpicker @selected="selected1"></v-distpicker>
              </template>
            </el-form-item>
            <el-form-item label="健康状况" prop="healthStatus">
              <el-select v-model="allInfo.healthStatus">
                <el-option label="良好" value="good"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="户口性质" prop="accountNature">
              <el-select v-model="allInfo.accountNature" placeholder="请选择">
                <el-option label="农户" value="rural"></el-option>
                <el-option label="非农户" value="NOrural"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="客户标签" prop="customerLabel">
              <el-select v-model="allInfo.customerLabel" placeholder="请选择">
                <el-option label="资源户" value="resource"></el-option>
                <el-option label="非资源户" value="NOresource"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="经办客户经理" prop="responsible">
              <el-select v-model="allInfo.responsible"  placeholder="请选择">
                <el-option label="张三" value="张三"></el-option>
                <el-option label="李四" value="李四"></el-option>
                <el-option label="王五" value="王五"></el-option>
                <el-option label="赵六" value="赵六"></el-option>
              </el-select>
            </el-form-item>
          </el-form>
        </el-tab-pane>
        <el-tab-pane label="家庭信息>>">
          <span>家庭信息</span>
          <el-form :model="allInfo" :rules="rules" ref="ruleForm" label-position="top" style="width:800px;margin-left: 100px;padding-top: 10px" label-width="100px" class="demo-ruleForm" lable="家庭信息">
            <el-form-item label="婚姻状况">
              <el-radio-group v-model="allInfo.maritalStatus">
                <el-radio label="未婚"></el-radio>
                <el-radio label="已婚"></el-radio>
                <el-radio label="离异"></el-radio>
                <el-radio label="丧偶"></el-radio>
              </el-radio-group>
            </el-form-item>
            <el-form-item   label="家庭人数" prop="familySize">
              <el-input v-model="allInfo.familySize" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="家庭情况概况" prop="familyStatus">
              <el-input type="textarea" v-model="allInfo.familyStatus" placeholder="请简要描述家庭情况"></el-input>
            </el-form-item>
          </el-form>
        </el-tab-pane>
        <el-tab-pane label="居住信息>>">
          <span>居住信息</span>
          <el-form :model="allInfo" :rules="rules" ref="ruleForm" label-position="top" style="width:800px;margin-left: 100px;padding-top: 10px" label-width="100px" class="demo-ruleForm" lable="居住信息">
            <el-form-item label="居住地址" prop="residentialAddress">
              <template>
                <v-distpicker @selected="selected2"></v-distpicker>
              </template>
            </el-form-item>
            <el-form-item label="详细地址" prop="address">
              <el-input v-model="allInfo.address" placeholder="请具体到街道小区/村组"></el-input>
            </el-form-item>
            <el-form-item label="居住状态" prop="residenceStatus">
              <el-select v-model="allInfo.residenceStatus" placeholder="请选择">
                <el-option label="自购无贷" value="noLoan"></el-option>
                <el-option label="自购按揭" value="mortgage"></el-option>
                <el-option label="集体宿舍" value="dormitory"></el-option>
                <el-option label="租房" value="Renting"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="居住年限" prop="lengthOfResidence">
              <el-input-number v-model="allInfo.lengthOfResidence" controls-position="right" :min="1"></el-input-number>
            </el-form-item>
          </el-form>
        </el-tab-pane>
        <el-tab-pane label="就业信息>>">
          <span>就业信息</span>
          <el-form :model="allInfo" :rules="rules" ref="ruleForm" label-position="top" style="width:800px;margin-left: 100px;padding-top: 10px" label-width="100px" class="demo-ruleForm" lable="就业信息">
            <el-form-item label="单位名称" prop="companyName">
              <el-input v-model="allInfo.companyName" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="单位电话" prop="workPhone">
              <el-input v-model="allInfo.workPhone" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="单位地址" prop="unitAddress">
              <template>
                <v-distpicker @selected="selected3"></v-distpicker>
              </template>
            </el-form-item>
            <el-form-item label="详细地址" prop="unitDetailAddress">
              <el-input v-model="allInfo.unitDetailAddress" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="行业类型" prop="industryType" size="120px">
              <el-select v-model="allInfo.industryType" placeholder="请选择" >
                <el-option label="农、林、牧、渔业" value="agriculture"></el-option>
                <el-option label="采矿业" value="mining"></el-option>
                <el-option label="制造业" value="manufacturing"></el-option>
                <el-option label="电力、热力、燃气以及水生产和供效应" value="power"></el-option>
                <el-option label="建筑业" value="construction"></el-option>
                <el-option label="信息传输、软件和信息技术服务业" value="infomation"></el-option>
                <el-option label="金融业" value="finance"></el-option>
                <el-option label="房地产业" value="realEstate "></el-option>
                <el-option label="租赁和商务服务业" value="leasing"></el-option>
                <el-option label="科学研究和技术服务业" value="scientificResearch"></el-option>
                <el-option label="水利、环境和公共设施管理业" value="waterConservancy"></el-option>
                <el-option label="居民服务、修理和其他服务业" value="residentServices"></el-option>
                <el-option label="教育" value="education"></el-option>
                <el-option label="卫生和社会工作" value="hygienism"></el-option>
                <el-option label="文化、体育和娱乐业" value="culture"></el-option>
                <el-option label="公共管理、社会保障和社会组织" value="publicManagement"></el-option>
                <el-option label="国际组织" value="internationalOrganization"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="职业" prop="profession" >
              <el-select v-model="allInfo.profession" placeholder="请选择">
                <el-option label="办事人员和有关人员" value="handler"></el-option>
                <el-option label="社会生产服务和生活服务人员" value="serviceStaff"></el-option>
                <el-option label="军人" value="soldier"></el-option>
                <el-option label="党的机关、国家机关、群众团体和社会组织、企业单位负责人" value="leader"></el-option>
                <el-option label="农、林、牧、渔业生产及辅助人员" value="famer"></el-option>
                <el-option label="专业技术人员" value="technicalPersonnel"></el-option>
                <el-option label="生产制造及有关人员" value="manufacturingPersonnel"></el-option>
                <el-option label="其他不便分类的工作人员" value="others"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="职务" prop="position" >
              <el-select v-model="allInfo.position" placeholder="请选择">
                <el-option label="一般员工" value="generalStaff"></el-option>
                <el-option label="中层领导" value="middleLeaders"></el-option>
                <el-option label="高层领导" value="senioreaders"></el-option>
                <el-option label="企业主" value="businessOwners"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="工作年限" prop="workingYears">
              <el-input-number v-model="allInfo.workingYears" controls-position="right" :min="0"></el-input-number>
            </el-form-item>
            <el-form-item label="年薪" prop="annualSalary">
              <el-input v-model="allInfo.annualSalary" placeholder="请输入">
                <i slot="suffix" style="font-style:normal;margin-right: 20px;">万元</i>
              </el-input>
            </el-form-item>
          </el-form>
        </el-tab-pane>
        <el-tab-pane label="经济状况>>">
          <span>经济状况</span>
          <el-form :model="allInfo" :rules="rules" ref="ruleForm" label-position="top" style="width:800px;margin-left: 100px;padding-top: 10px" label-width="140px" class="demo-ruleForm" lable="经济状况">
            <el-form-item label="家庭月收入" prop="familyMonthlyIncome">
              <el-input v-model="allInfo.familyMonthlyIncome" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="抚养人数" prop="numberOfDependents">
              <el-input v-model="allInfo.numberOfDependents" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="资产与负债比" prop="assetsToLiabilitiesRatio">
              <el-input v-model="allInfo.assetsToLiabilitiesRatio" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="收入还贷比" prop="loanToIncomeRatio">
              <el-input v-model="allInfo.loanToIncomeRatio" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="个人年平均收入" prop="averagePersonalIncome">
              <el-input v-model="allInfo.averagePersonalIncome" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="月还款额与月可支配收入比值" prop="repaymentToIncomeRatio">
              <el-input v-model="allInfo.repaymentToIncomeRatio" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="家庭财产评估值" prop="familyPropertyAssessment">
              <el-input v-model="allInfo.familyPropertyAssessment" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="债务覆盖率" prop="debtCoverageRatio">
              <el-input v-model="allInfo.debtCoverageRatio" placeholder="请输入"></el-input>
            </el-form-item>
          </el-form>
        </el-tab-pane>
        <el-tab-pane label="信用状况">
          <span>信用状况</span>
          <el-form :model="allInfo" :rules="rules" ref="ruleForm" label-position="top" style="width:800px;margin-left: 100px;padding-top: 10px" label-width="140px" class="demo-ruleForm" lable="信用状况">
            <el-form-item label="还款记录" prop="repaymentRecord">
              <el-input v-model="allInfo.repaymentRecord" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="个人贷款或信用卡记录和年限" prop="recordsAndYears">
              <el-input v-model="allInfo.recordsAndYears" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="违约情况" prop="breachOfContract">
              <el-input v-model="allInfo.breachOfContract" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="信用卡透支情况等方面的详细调查" prop="overdraftSituation">
              <el-input v-model="allInfo.overdraftSituation" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="银行卡持有情况及银行账户情况" prop="bankCardSituation" >
              <el-input v-model="allInfo.bankCardSituation" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="个人贷款或信用卡违约情况" prop="creditCardDefault">
              <el-input v-model="allInfo.creditCardDefault" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="公安司法的不良记录" prop="judicialRecords">
              <el-input v-model="allInfo.judicialRecords" placeholder="请输入"></el-input>
            </el-form-item>
            <el-form-item label="个人信用度评分" prop="creditScore">
              <el-input v-model="allInfo.creditScore" placeholder="请输入"></el-input>
            </el-form-item>
          </el-form>
        </el-tab-pane>
      </el-tabs>
    <div style="margin-bottom: 100px;margin-top: 50px">
      <el-button type="primary" round style="margin-left: 380px"  @click="addNew(allInfo)">提交客户信息</el-button>
      <el-button type="danger" round   @click="cancel">取消</el-button>
    </div>
  </div>
</template>

<script>
 import VDistpicker from 'v-distpicker';
import { addCustomer } from "@/api/customer";

 export default {
   components: { VDistpicker },
   data() {
     return {
       allInfo: {
         id: '',
         name: '',
         channelSource: '',
         responsible: '',
         formerName: '无',
         idNumber: '',
         sex: '',
         phone: '',
         educational: '',
         residenceAddress: '',
         healthStatus: '',
         accountNature: '',
         customerLabel: '',
         deleteStatus: 0,
         completeStatus: '待完成',
         maritalStatus: '',
         familySize: '',
         familyStatus: '',
         residentialAddress: '',
         address: '',
         residenceStatus: '',
         lengthOfResidence: '1',
         companyName: '',
         workPhone: '',
         unitAddress: '',
         unitDetailAddress: '',
         industryType: '',
         profession: '',
         position: '',
         workingYears: '',
         annualSalary: '',
         familyMonthlyIncome: '',
         numberOfDependents: '',
         assetsToLiabilitiesRatio: '',
         loanToIncomeRatio: '',
         averagePersonalIncome: '',
         repaymentToIncomeRatio: '',
         familyPropertyAssessment: '',
         debtCoverageRatio: '',
         repaymentRecord: '',
         recordsAndYears: '',
         breachOfContract: '',
         overdraftSituation: '',
         bankCardSituation: '',
         creditCardDefault: '',
         judicialRecords: '',
         creditScore: '',
       },
       active: '0',
       rules: {
         channelSource: {
           required: true,
           message: '请输入'
         },
         name: {
           required: true,
           message: '请输入'
         },
         idNumber: [
           {required: true, message: '请填写证件号码', trigger: 'blur'},
           {
             pattern: /(^[1-9]\d{5}(18|19|([23]\d))\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$)|(^[1-9]\d{5}\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{2}$)/,
             message: '证件号码格式有误！',
             trigger: 'blur'
           }
         ],
         phone: [
           {
             required: true,
             message: '请输入手机号',
             trigger: 'blur'
           },
           {
             pattern: /^1[3|4|5|7|8][0-9]{9}$/,
             message: '手机号格式不对',
             trigger: 'blur'
           }
         ]
       }
     }
   },
   methods: {
     addNew: function (data) {
     if(this.allInfo.channelSource ==''){
       alert("请填写渠道来源相关信息！")
       return
     }else{
       if(this.allInfo.name ==''){
         alert("请填写用户姓名！")
         return
       }else{
         if(/(^[1-9]\d{5}(18|19|([23]\d))\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$)|(^[1-9]\d{5}\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{2}$)/.test(this.allInfo.idNumber)){
         }else if(this.allInfo.idNumber ==''){
           alert("请输入身份证号！")
           return
         }else {
           alert("请检查，身份证号输入有误！")
           return
         }
         if(/^1[3|4|5|7|8][0-9]{9}$/.test(this.allInfo.phone)){
         }else if(this.allInfo.phone == ''){
           alert("请输入手机号码")
           return
         }else {
           alert("请检查，手机号码输入有误！")
           return
         }
       }
      }
         var isnull =true
       console.log(this.allInfo)
         for (var val in this.allInfo) {
           if (this.allInfo[val] == '') {
             isnull = false
             this.$confirm('检测到未填写的内容，是否在离开页面前保存修改？', '确认信息', {
               distinguishCancelAndClose: true,
               confirmButtonText: '保存',
               cancelButtonText: '继续编辑'
             })
               .then(() => {
                 addCustomer(data).then((res) => {
                   this.$router.go(-1);
                   this.$message({
                     type: 'info',
                     message: '保存成功'
                   });
                 })
               })
               .catch(action => {
                 this.$message({
                   type: 'info',
                   message: action === 'cancel'
                     ? '放弃保存'
                     : '回到当前页面'
                 })
               });
           }
         }
       if(isnull){
         this.$confirm('已完成信息填写', '确认信息', {
           distinguishCancelAndClose: true,
           confirmButtonText: '保存',
           cancelButtonText: '继续编辑'
         })
           .then(() => {
             this.allInfo.completeStatus='已完成'
             addCustomer(data).then((res) => {
               this.$router.go(-1);
               this.$message({
                 type: 'info',
                 message: '保存成功'
               });
             })
           })
           .catch(action => {
             this.$message({
               type: 'info',
               message: action === 'cancel'
                 ? '放弃保存并停留在当前页面'
                 : '停留在当前页面'
             })
           })
       }
     },
     cancel: function () {
       this.$confirm('检测到未保存的内容，是否在离开页面前保存修改？', '确认信息', {
         distinguishCancelAndClose: true,
         confirmButtonText: '保存',
         cancelButtonText: '放弃'
       })
         .then(() => {
           this.$router.go(-1)
           this.$message({
             type: 'info',
             message: '保存修改'

           });
         })
         .catch(action => {
           this.$router.go(-1)
           this.$message({
             type: 'info',
             message: action === 'cancel'
               ? '放弃保存并离开页面'
               : '停留在当前页面'
           })
         });
     },
     next() {
       if (this.active++ > 2) this.active = 0
     },
     selected1(data){
       this.allInfo.residenceAddress=data.province.value +''+ data.city.value + data.area.value
     },
     selected2(data){
       this.allInfo.residentialAddress=data.province.value +''+ data.city.value + data.area.value
       console.log( this.allInfo.residentialAddress)
     },
     selected3(data){
       this.allInfo.unitAddress=data.province.value +''+ data.city.value + data.area.value
       console.log( this.allInfo.unitAddress)

     }
   }
 }
</script>
<style scoped>
</style>
