<template>
  <div id="app">
    <div class="el-box">
      <el-form :model="ruleFormA" :rules="rules" ref="ruleFormA" label-width="100px" class="demo-ruleForm">
        <el-form-item label="version" prop="version">
          <el-input v-model="ruleFormA.version" placeholder="SimpleWallet的版本信息，如1.0"></el-input>
        </el-form-item>
        <el-form-item label="appName" prop="appName">
          <el-input v-model="ruleFormA.appName" placeholder="Dapp名字"></el-input>
        </el-form-item>
        <el-form-item label="appIcon" prop="appIcon">
          <el-input v-model="ruleFormA.appIcon" placeholder="Dapp图标"></el-input>
        </el-form-item>
        <el-form-item label="action" prop="action">
          <el-input v-model="ruleFormA.action" placeholder="赋值为login"></el-input>
        </el-form-item>
        <el-form-item label="uuID" prop="uuID">
          <el-input v-model="ruleFormA.uuID" placeholder="Dapp server生成的，用于此次登录验证的唯一标识"></el-input>
        </el-form-item>
        <el-form-item label="loginUrl" prop="loginUrl">
          <el-input v-model="ruleFormA.loginUrl" placeholder="Dapp server上用于登录验证信息的url"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleFormA')">立即创建</el-button>
          <el-button @click="resetForm('ruleFormA')">重置</el-button>
        </el-form-item>
      </el-form>
      <QRCode v-show="showCode" :text="qrCode"></QRCode>

      <el-form :model="ruleFormB" :rules="rules" ref="ruleFormB" label-width="100px" class="demo-ruleForm">
        <el-form-item label="version" prop="version">
          <el-input v-model="ruleFormB.version" placeholder="SimpleWallet的版本信息，如1.0"></el-input>
        </el-form-item>
        <el-form-item label="timestamp" prop="timestamp">
          <el-input v-model="ruleFormB.timestamp" placeholder="当前UNIX时间戳"></el-input>
        </el-form-item>
        <el-form-item label="sign" prop="sign">
          <el-input v-model="ruleFormB.sign" placeholder="eos签名"></el-input>
        </el-form-item>
        <el-form-item label="uuID" prop="uuID">
          <el-input v-model="ruleFormB.uuID" placeholder="Dapp server生成的，用于此次登录验证的唯一标识"></el-input>
        </el-form-item>
        <el-form-item label="account" prop="account">
          <el-input v-model="ruleFormB.account" placeholder="eos账户名"></el-input>
        </el-form-item>
        <el-form-item label="ref" prop="ref">
          <el-input v-model="ruleFormB.ref" placeholder="来源,如钱包名"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm_v2('ruleFormB')">立即创建</el-button>
          <el-button @click="resetForm('ruleFormB')">重置</el-button>
        </el-form-item>
      </el-form>

      <el-form :model="ruleFormC" :rules="rules" ref="ruleFormC" label-width="100px" class="demo-ruleForm">
        <el-form-item label="version" prop="version">
          <el-input v-model="ruleFormC.version" placeholder="SimpleWallet的版本信息，如1.0"></el-input>
        </el-form-item>
        <el-form-item label="appName" prop="appName">
          <el-input v-model="ruleFormC.appName" placeholder="Dapp名字"></el-input>
        </el-form-item>
        <el-form-item label="appIcon" prop="appIcon">
          <el-input v-model="ruleFormC.appIcon" placeholder="Dapp图标"></el-input>
        </el-form-item>
        <el-form-item label="action" prop="action">
          <el-input v-model="ruleFormC.action" placeholder="赋值为login"></el-input>
        </el-form-item>
        <el-form-item label="uuID" prop="uuID">
          <el-input v-model="ruleFormC.uuID" placeholder="Dapp server生成的，用于此次登录验证的唯一标识"></el-input>
        </el-form-item>
        <el-form-item label="loginUrl" prop="loginUrl">
          <el-input v-model="ruleFormC.loginUrl" placeholder="Dapp server上用于登录验证信息的url"></el-input>
        </el-form-item>
        <el-form-item label="appKey" prop="appKey">
          <el-input v-model="ruleFormC.appKey" placeholder="钱包回调拉起Dapp移动端的app标识"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm_v3('ruleFormC')">立即创建</el-button>
          <el-button @click="resetForm('ruleFormC')">重置</el-button>
        </el-form-item>
      </el-form>


    </div>
  </div>
</template>
<style>
  .el-box{
    width: 800px;
    margin: auto;
  }
</style>
<script>
    import ElFormItem from "../node_modules/element-ui/packages/form/src/form-item.vue";
    import ElInput from "../node_modules/element-ui/packages/input/src/input.vue";
    import QRCode from "./components/QRCode";
    export default {
        components: {
            ElInput,
            ElFormItem,
            QRCode
        },
        data() {
            return {
                showCode: false,
                qrCode: '',
                ruleFormA: {
                    version: '',
                    appName: '',
                    appIcon: '',
                    action: '',
                    uuID: '',
                    loginUrl: '',
                    timestamp: '',
                    sign: '',
                    account: '',
                    ref: ''
                },
                ruleFormB: {
                    version: '',
                    appName: '',
                    appIcon: '',
                    action: '',
                    uuID: '',
                    loginUrl: '',
                    timestamp: '',
                    sign: '',
                    account: '',
                    ref: ''
                },
                ruleFormC: {
                    version: '',
                    appName: '',
                    appIcon: '',
                    action: '',
                    uuID: '',
                    loginUrl: '',
                    timestamp: '',
                    sign: '',
                    account: '',
                    ref: '',
                    appKey: '',
                },
                rules: {
                    version: [
                        { required: true, message: 'version不能为空', trigger: 'blur' },
                    ],
                    appName: [
                        { required: true, message: 'appName不能为空', trigger: 'blur' },
                    ],
                    appIcon: [
                        { required: true, message: 'appIcon不能为空', trigger: 'blur' },
                    ],
                    action: [
                        { required: true, message: 'action不能为空', trigger: 'blur' },
                    ],
                    uuID: [
                        { required: true, message: 'uuID不能为空', trigger: 'blur' },
                    ],
                    loginUrl: [
                        { required: true, message: 'loginUrl不能为空', trigger: 'blur' },
                    ],
                    timestamp: [
                        { required: true, message: 'timestamp不能为空', trigger: 'blur' },
                    ],
                    sign: [
                        { required: true, message: 'eos签名不能为空', trigger: 'blur' },
                    ],
                    account: [
                        { required: true, message: 'eos账户名不能为空', trigger: 'blur' },
                    ],
                    ref: [
                        { required: true, message: '来源,如钱包名不能为空', trigger: 'blur' },
                    ],
                    appKey: [
                        { required: true, message: 'app标识不能为空', trigger: 'blur' },
                    ]


                }
            };
        },
        methods: {
            submitForm(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        this.showCode = true;
                        this.qrCode = JSON.stringify(this.ruleFormA);
                        alert('submit!');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            },
            submitForm_v2(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            },
            submitForm_v3(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            },
            resetForm(formName) {
                this.showCode = false;
                this.$refs[formName].resetFields();
            }
        }
    }
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
</style>
