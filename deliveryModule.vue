<!--   寄递方式   Developed by FengYingying
  引用：
       创建集邮普通商品
 -->
<template>
  <div class="deliveryModule">
       <el-form  label-width="15%">
           <el-form-item label="请选择寄递方式" required>   
      
                <div>
                  <div style="width:85%;margin-top: 30px;">
                    <!-- this.$route.query.isCollaboration=='1' -->
                    <el-checkbox v-model="checked0" :disabled="this.isSelfMentions==0||AA0==1?true:false" label="1" @change="handleChecked">网点自提</el-checkbox><br/>
                  </div>
                  <div style="color:red;font-size:12px;" v-show="this.$route.query.userLevel==0"> 注意：普通寄递、集中寄递、分级寄递只能三选一 ！</div> 
                  <!-- <div style="width:15%;float:left;"> -->
                    <!-- ||this.skuItem.isSubStock==3 -->
                    <!-- <el-checkbox style="height:75px;" v-model="checked7"  @change="independent" v-show="this.$route.query.userLevel==0" label="2">普通寄递</el-checkbox><br/>
                    <el-checkbox style="height:75px;" v-model="checked8" @change="concentrated" v-show="this.$route.query.userLevel==0" label="3">集中寄递</el-checkbox><br/> 
                    <el-checkbox style="height:75px;" v-model="checked9"  @change="subordinate" v-show="this.$route.query.userLevel==0" label="4">分级寄递</el-checkbox> -->
                    <!-- <label for="" style="display:block;height:75px;">普通寄递</label> -->
                    <!-- <label for="" style="display:block;height:75px;" v-show="this.$route.query.userLevel==0">集中寄递</label>
                    <label for="" style="display:block;" v-show="this.$route.query.userLevel==0">分级寄递</label> -->
                  <!-- </div> -->
                   <div  class="consign-box" id="row">
                      <el-row >
                          <div style="float:left;margin-right:15px;line-height: 20px;">普通寄递</div>
                        <el-col :span="4"><div class="grid-content bg-purple">
                          <el-checkbox @change="isChange7" :disabled="this.skuItem.isSend==0||AA1==1?true:false"  v-model="checked1" label="1101">挂号信</el-checkbox>
                          <br/><label for="" >运费模板 :</label>
                          <el-select v-model="postageTemplate1" clearable  placeholder="请选择运费模板" :disabled="checked1==''"> 
                            <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                          </el-select> </div>
                        </el-col>
                        <el-col :span="4"><div class="grid-content bg-purple">
                            <el-checkbox @change="isChange7" :disabled="this.skuItem.isSend==0||AA2==1?true:false"  v-model="checked2" label="1102" >邮政小包</el-checkbox>
                            <br/><label for="" >运费模板 :</label>
                            <el-select v-model="postageTemplate2" clearable   placeholder="请选择运费模板" :disabled="checked2==''"> 
                              <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                            </el-select>  
                        </div>
                      </el-col>
                        <el-col :span="4"><div class="grid-content bg-purple">
                            <el-checkbox @change="isChange7" :disabled="this.skuItem.isSend==0||AA3==1?true:false"  v-model="checked3" label="1103" >EMS</el-checkbox>
                            <br/><label for="" >运费模板 :</label>
                            <el-select v-model="postageTemplate3" clearable   placeholder="请选择运费模板" :disabled="checked3==''"> 
                              <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                            </el-select>  
                        </div>
                      </el-col>
                      </el-row>
                    <!-- </div>
                    //集中寄递
                   <div  class="consign-box"> -->
                      <el-row v-show="this.$route.query.userLevel==0">
                        <div v-show="this.$route.query.userLevel==0" style="float:left;margin-right:15px;line-height: 20px;">集中寄递</div>
                        <el-col :span="4"><div class="grid-content bg-purple">
                          <el-checkbox @change="isChange8" :disabled="this.skuItem.isSend==0||AA4==1?true:false"  v-model="checked4" label="1101">挂号信</el-checkbox>
                          <br/><label for="" >运费模板 :</label>
                          <el-select v-model="postageTemplate4" clearable   placeholder="请选择运费模板" :disabled="checked4==''"> 
                            <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                          </el-select> </div>
                        </el-col>
                        <el-col :span="4"><div class="grid-content bg-purple">
                            <el-checkbox @change="isChange8" :disabled="this.skuItem.isSend==0||AA5==1?true:false"  v-model="checked5" label="1102" >邮政小包</el-checkbox>
                            <br/><label for="" >运费模板 :</label>
                            <el-select v-model="postageTemplate5" clearable   placeholder="请选择运费模板" :disabled="checked5==''"> 
                              <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                            </el-select>  
                        </div>
                      </el-col>
                        <el-col :span="4"><div class="grid-content bg-purple">
                            <el-checkbox @change="isChange8" :disabled="this.skuItem.isSend==0||AA6==1?true:false"  v-model="checked6" label="1103" >EMS</el-checkbox>
                            <br/><label for="" >运费模板 :</label>
                            <el-select v-model="postageTemplate6" clearable placeholder="请选择运费模板" :disabled="checked6==''"> 
                              <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                            </el-select>  
                        </div>
                      </el-col>
                      </el-row>
                    <!-- 分级寄递 -->
                      <el-row v-show="this.$route.query.userLevel==0">
                        <div v-show="this.$route.query.userLevel==0" style="float:left;margin-right:15px;line-height: 20px;">分级寄递</div>
                        <el-col :span="4"><div class="grid-content bg-purple">
                          <el-checkbox @change="isChange9" :disabled="this.skuItem.isSend==0||AA7==1?true:false"  v-model="checked10" label="1101">挂号信</el-checkbox>
                          <br/><label for="" >运费模板 :</label>
                          <el-select v-model="postageTemplate7" clearable   placeholder="请选择运费模板" :disabled="checked10==''"> 
                            <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                          </el-select> </div>
                        </el-col>
                        <el-col :span="4"><div class="grid-content bg-purple">
                            <el-checkbox @change="isChange9" :disabled="this.skuItem.isSend==0||AA8==1?true:false"  v-model="checked11" label="1102" >邮政小包</el-checkbox>
                            <br/><label for="" >运费模板 :</label>
                            <el-select v-model="postageTemplate8" clearable   placeholder="请选择运费模板" :disabled="checked11==''"> 
                              <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                            </el-select>  
                        </div>
                      </el-col>
                        <el-col :span="4"><div class="grid-content bg-purple">
                            <el-checkbox @change="isChange9" :disabled="this.skuItem.isSend==0||AA9==1?true:false"  v-model="checked12" label="1103" >EMS</el-checkbox>
                            <br/><label for="" >运费模板 :</label>
                            <el-select v-model="postageTemplate9" clearable placeholder="请选择运费模板" :disabled="checked12==''"> 
                              <el-option v-for='(postItem,postIndex) in postageTemplateList' :label="postItem.templateName"   :value="postItem.id" :key='postIndex'></el-option>
                            </el-select>  
                        </div>
                      </el-col>
                      </el-row>
                    </div>
                </div>
            </el-form-item>
       </el-form>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        isSelfMentions:'',
        postIsShow:false,    //运费模板详情是否展示
				postageTempDetail:{},
        postageTemplate1:'',
        postageTemplate2:'',
        postageTemplate3:'',
        postageTemplate4:'',
        postageTemplate5:'',
        postageTemplate6:'',
        postageTemplate7:'',
        postageTemplate8:'',
        postageTemplate9:'',
				postageTemplateList:[], //运费模板列表
				postageTemplateListUrl: process.env.MER_WEB_URL + "/lgt/postagetemplate/list",//查询运费模板列表
        postageTemplateDetailUrl:process.env.MER_WEB_URL+'/lgt/postagetemplate/view/',//根据ID查询运费模板详情
        skudispatch:process.env.MER_WEB_URL+'/gcc/skudispatch/list',//查询寄递方式
        listUrl: process.env.MER_WEB_URL + "/lgt/selfservicesite/list",//查询自提点
        flag:false,  //处理异步





        checked0:false,
        checked1:false,
        checked2:false,
        checked3:false,
        checked4:false,
        checked5:false,
        checked6:false,
        checked7:false,
        checked8:false,
        checked9:false,
        checked10:false,
        checked11:false,
        checked12:false,
        dispatchType:'',//暂时的变量
        dispatchModeCode:'',//暂时的变量
        gccSkuConsignment:[],
        tempflag:false,
        AA0:false,
        AA1:false,
        AA2:false,
        AA3:false,
        AA4:false,
        AA5:false,
        AA6:false,
        AA7:false,
        AA8:false,
        AA9:false,
      }
    },
    props: {
      skuItem: Object,
      required: true
    },
    created() {
      this.isChecked()
      this.getList()
    },
    computed: {
      gccSkuDispatchModes(){
        return this.skuItem.gccSkuDispatchModes;
      },
    },
    watch:{
      // gccSkuDispatchModes(){
      //    this.clearDeliver()
      //    this.getList()
      // },
      //深度监控全国预售和普通预售
      skuItem:{
        immediate: true,
        handler(newValue, oldValue) {
    //       console.log(newValue) 
    // 　　  console.log(newValue.isSelfMention,newValue.isSend,newValue.isSubStock)　
          this.clearDeliver()
          this.getList()
　　　　},
　　　　deep: true
      }
    },
    methods: {
      getList(){
        this.$nextTick(() => {
            console.log('自提'+this.skuItem.isSelfMention,'寄递'+this.skuItem.isSend,'预售'+this.skuItem.isSubStock)　
            this.isSelfMentions = this.skuItem.isSelfMention;
        })
        //这个判断是自建商品和修改自建都不调用这个方法的判断    
        // createNormal   创建商品的路由  jyNewCreate  自建商品  
        console.log(this.skuItem)
        console.log(this.skuItem.tempProdGoodsType)
        // this.skuItem.tempProdGoodsType   
        // PRE_SALE_ALL   自建全国预售     PRE_SALE自建普通预售
        // if(this.skuItem.tempProdGoodsType!=='PRE_SALE'){//!=jyNewCreate  就是创建商品  
        // console.log(this.$route.query.pageState) 
        // pageState=edit  修改    pageState=new  创建  
        let paramsud = {
            'spuId': this.$route.query.pageState=='edit'?this.skuItem.poolSpuId:this.skuItem.spuId,
            'skuId': this.$route.query.pageState=='edit'?this.skuItem.poolSkuId:this.skuItem.skuId,
            //自建0
            'isCollaboration': this.skuItem.tempProdGoodsType=='PRE_SALE'?'0':this.$route.query.isCollaboration,
            'isSubStock': this.skuItem.isSubStock,
            'prodGoodsType': this.$route.query.prodGoodsType,
          };
        this.$axios.post(this.skudispatch, paramsud).then((res) => {
          if (res.data.retCode === '1') {
            console.log(res.data.data)
            res.data.data.forEach((item,index)=>{
              if(item.dispatchType==1){//=1说明是自提
                if(item.field1==0){//=0 自提不可勾选
                  this.AA0=1;
                }else if(item.field1==1){//=0 自提可勾选
                  this.AA0=0;
                }
              }else{//说明是寄递
                if(item.dispatchType==2){//=2说明是普通寄递
                  item.gccSkuDispatchModes.forEach((itemType,index)=>{
                    if(itemType.dispatchModeCode=='1101'&&itemType.dispatchType=='2'){
                      if(itemType.field1==0){//=0 普通寄递-挂号信 不可勾选
                        this.AA1=1;    //不能等于0  因为0就是false
                      }else if(itemType.field1==1){//=1 普通寄递-挂号信 可勾选
                        this.AA1=0;
                      }
                    }
                    if(itemType.dispatchModeCode=='1102'&&itemType.dispatchType=='2'){
                      if(itemType.field1==0){//=0 普通寄递-邮政小包 不可勾选
                        this.AA2=1;
                      }else if(itemType.field1==1){//=1 普通寄递-邮政小包 可勾选
                        this.AA2=0;
                      }
                    }
                    if(itemType.dispatchModeCode=='1103'&&itemType.dispatchType=='2'){
                      if(itemType.field1==0){//=0 普通寄递-"EMS" 不可勾选
                        this.AA3=1;
                      }else if(itemType.field1==1){//=1 普通寄递-"EMS" 可勾选
                        this.AA3=0;
                      }
                    }
                  })
                }
                if(item.dispatchType==3){//=3说明是集中寄递
                  item.gccSkuDispatchModes.forEach((itemType,index)=>{
                    if(itemType.dispatchModeCode=='1101'&&itemType.dispatchType=='3'){
                      if(itemType.field1==0){//=0 集中寄递-挂号信 不可勾选
                        this.AA4=1;
                      }else if(itemType.field1==1){//=1 集中寄递-挂号信 可勾选
                        this.AA4=0;
                      }
                    }
                    if(itemType.dispatchModeCode=='1102'&&itemType.dispatchType=='3'){
                      if(itemType.field1==0){//=0 集中寄递-邮政小包 不可勾选
                        this.AA5=1;
                      }else if(itemType.field1==1){//=1 集中寄递-邮政小包 可勾选
                        this.AA5=0;
                      }
                    }
                    if(itemType.dispatchModeCode=='1103'&&itemType.dispatchType=='3'){
                      if(itemType.field1==0){//=0 集中寄递-"EMS" 不可勾选
                        this.AA6=1;
                      }else if(itemType.field1==1){//=1 集中寄递-"EMS" 可勾选
                        this.AA6=0;
                      }
                    }
                  })
                }
                if(item.dispatchType==4){//=4说明是分级寄递
                  item.gccSkuDispatchModes.forEach((itemType,index)=>{
                    if(itemType.dispatchModeCode=='1101'&&itemType.dispatchType=='4'){
                      if(itemType.field1==0){//=0 分级寄递-挂号信 不可勾选
                        this.AA7=1;
                      }else if(itemType.field1==1){//=1 分级寄递-挂号信 可勾选
                        this.AA7=0;
                      }
                    }
                    if(itemType.dispatchModeCode=='1102'&&itemType.dispatchType=='4'){
                      if(itemType.field1==0){//=0 分级寄递-邮政小包 不可勾选
                        this.AA8=1;
                      }else if(itemType.field1==1){//=1 分级寄递-邮政小包 可勾选
                        this.AA8=0;
                      }
                    }
                    if(itemType.dispatchModeCode=='1103'&&itemType.dispatchType=='4'){
                      if(itemType.field1==0){//=0 分级寄递-"EMS" 不可勾选
                        this.AA9=1;
                      }else if(itemType.field1==1){//=1 分级寄递-"EMS" 可勾选
                        this.AA9=0;
                      }
                    }
                  })
                }
              }
            })
          } else {
            this.$message.error(res.data.retMessage);
          }
        });
        // }
      },
      clearDeliver(){
        this.$nextTick(() => {
            console.log('自提'+this.skuItem.isSelfMention,'寄递'+this.skuItem.isSend,'预售'+this.skuItem.isSubStock)　
            this.isSelfMentions = this.skuItem.isSelfMention;
        })
        console.log(this.skuItem)
        if(this.$route.name=='jyNewCreate'){//自建
          this.checked0=false;
          this.checked1=false;
          this.checked2=false;
          this.checked3=false;
          this.checked4=false;
          this.checked5=false;
          this.checked6=false;
          this.checked7=false;
          this.checked8=false;
          this.checked9=false;
          this.checked10=false;
          this.checked11=false;
          this.checked12=false;
          this.postageTemplate1='';
          this.postageTemplate2='';
          this.postageTemplate3='';
          this.postageTemplate4='';
          this.postageTemplate5='';
          this.postageTemplate6='';
          this.postageTemplate7='';
          this.postageTemplate8='';
          this.postageTemplate9='';
          this.isChecked()
        }
      },
      isChecked(){
      this.initData();
      // console.log(this.$route.query.userLevel)
      // console.log('自提'+this.skuItem.isSelfMention,'寄递'+this.skuItem.isSend,'预售'+this.skuItem.isSubStock)　
        if(this.$route.query.isCollaboration=='1'){//==1协同属于创建时不可更改
          if(this.gccSkuDispatchModes==null||this.gccSkuDispatchModes==[]){
          }else if(this.gccSkuDispatchModes.length!==0){//!==0说明协同商品有推送寄递方式
            this.gccSkuDispatchModes.forEach((item, index) => {//返显
              if(item.dispatchType=='1'){//==1说明是网点自提
                this.checked0=true;
              }else if(item.dispatchType=='2'){//==2：普通寄递（寄递）
                this.checked7=true;
              }else if(item.dispatchType=='3'){//==3：集中寄递（寄递）
                this.checked8=true;
              }else if(item.dispatchType=='4'){//==4：分级寄递（寄递）
                this.checked9=true;
              }
              // 挂号信：1101， 邮政小包：1102， EMS：1103
              if(item.dispatchModeCode=='1101'&&item.dispatchType=='2'){
                this.checked1=true;
                this.postageTemplate1 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1102'&&item.dispatchType=='2'){
                this.checked2=true;
                this.postageTemplate2 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1103'&&item.dispatchType=='2'){
                this.checked3=true;
                this.postageTemplate3 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1101'&&item.dispatchType=='3'){
                this.checked4=true;
                this.postageTemplate4 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1102'&&item.dispatchType=='3'){
                this.checked5=true;
                this.postageTemplate5 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1103'&&item.dispatchType=='3'){
                this.checked6=true;
                this.postageTemplate6 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1101'&&item.dispatchType=='4'){
                this.checked10=true;
                this.postageTemplate7 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1102'&&item.dispatchType=='4'){
                this.checked11=true;
                this.postageTemplate8 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1103'&&item.dispatchType=='4'){
                this.checked12=true;
                this.postageTemplate9 = item.postageTemplate;
              }
            })
              //为防止只推送普通寄递和集中寄递，分级寄递
            if(this.checked7==true&&this.checked1==false&&this.checked2==false&&this.checked3==false){
              this.$message.error("协同商品推送普通寄递方式有误");
              return false;
            }
            if(this.checked8==true&&this.checked4==false&&this.checked5==false&&this.checked6==false){
              this.$message.error("协同商品推送集中寄递方式有误");
              return false;
            }
            if(this.checked9==true&&this.checked10==false&&this.checked11==false&&this.checked12==false){
              this.$message.error("协同商品推送分级寄递方式有误");
              return false;
            }
          }
          // else{//说明协同商品没有推送寄递方式
          //   this.$message.error("协同商品未推送寄递方式");
          //   return false;
          // }
        }else if(this.$route.query.isCollaboration=='0'){//==0非协同属于修改时可更改或不可更改
          if(this.gccSkuDispatchModes==null||this.gccSkuDispatchModes==[]){
          }else if(this.gccSkuDispatchModes.length!==0){
            this.gccSkuDispatchModes.forEach((item, index) => {//返显
              if(item.dispatchType=='1'){//==1说明是网点自提
                this.checked0=true;
              }else if(item.dispatchType=='2'){//==2：普通寄递（寄递）
                this.checked7=true;
              }else if(item.dispatchType=='3'){//==3：集中寄递（寄递）
                this.checked8=true;
              }else if(item.dispatchType=='4'){//==4：分级寄递（寄递）
                this.checked9=true;
              }
              // 挂号信：1101， 邮政小包：1102， EMS：1103
              if(item.dispatchModeCode=='1101'&&item.dispatchType=='2'){
                this.checked1=true;
                this.postageTemplate1 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1102'&&item.dispatchType=='2'){
                this.checked2=true;
                this.postageTemplate2 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1103'&&item.dispatchType=='2'){
                this.checked3=true;
                this.postageTemplate3 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1101'&&item.dispatchType=='3'){
                this.checked4=true;
                this.postageTemplate4 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1102'&&item.dispatchType=='3'){
                this.checked5=true;
                this.postageTemplate5 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1103'&&item.dispatchType=='3'){
                this.checked6=true;
                this.postageTemplate6 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1101'&&item.dispatchType=='4'){
                this.checked10=true;
                this.postageTemplate7 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1102'&&item.dispatchType=='4'){
                this.checked11=true;
                this.postageTemplate8 = item.postageTemplate;
              }else if(item.dispatchModeCode=='1103'&&item.dispatchType=='4'){
                this.checked12=true;
                this.postageTemplate9 = item.postageTemplate;
              }
            })
          }
            //   为防止只推送普通寄递和集中寄递
            // if(this.checked7==true&&this.checked1==false&&this.checked2==false&&this.checked3==false){
            //   this.$message.error("商品普通寄递方式有误");
            //   return false;
            // }
            // if(this.checked8==true&&this.checked4==false&&this.checked5==false&&this.checked6==false){
            //   this.$message.error("商品集中寄递方式有误");
            //   return false;
            // }
        }
      },handleChecked(){//点击网点自提时，判断是否有自提点
        let params = {
					'pageNo': 1,
					'pageSize': 1,
					'businessLine': 'JY',
					'isEnable': 0,
				}
        this.$axios.post(this.listUrl,params).then((res)=>{
            if(res.data.retCode=='1'){
              if(res.data.data.items==[]||null){
                this.$message.error('需要维护至少一个自提点');
                this.checked0=false;
              }
            }else{
              this.$message.error(res.data.retMessage);
            }
        })
      },independent(){//普通寄递  全选
        if(this.checked7==true){
          this.checked1=true;
          this.checked2=true;
          this.checked3=true;
          this.postageTemplate1='';
          this.postageTemplate2='';
          this.postageTemplate3='';
        }else{
          this.checked1=false;
          this.checked2=false;
          this.checked3=false;
          this.postageTemplate1='';
          this.postageTemplate2='';
          this.postageTemplate3='';
        }
      },concentrated(){//集中寄递   全选
        if(this.checked8==true){
          this.checked4=true;
          this.checked5=true;
          this.checked6=true;
          this.postageTemplate4='';
          this.postageTemplate5='';
          this.postageTemplate6='';
        }else{
          this.checked4=false;
          this.checked5=false;
          this.checked6=false;
          this.postageTemplate4='';
          this.postageTemplate5='';
          this.postageTemplate6='';
        }
      },subordinate(){//分级寄递   全选
        if(this.checked9==true){
          this.checked10=true;
          this.checked11=true;
          this.checked12=true;
          this.postageTemplate7='';
          this.postageTemplate8='';
          this.postageTemplate9='';
        }else{
          this.checked10=false;
          this.checked11=false;
          this.checked12=false;
          this.postageTemplate7='';
          this.postageTemplate8='';
          this.postageTemplate9='';
        }
      },isChange7(oldValue){
        console.log(oldValue)
        if(oldValue){
          this.checked8=false;
          this.checked9=false;
          this.checked4=false;
          this.checked5=false;
          this.checked6=false;
          this.checked10=false;
          this.checked11=false;
          this.checked12=false;
          this.postageTemplate4='';
          this.postageTemplate5='';
          this.postageTemplate6='';
          this.postageTemplate7='';
          this.postageTemplate8='';
          this.postageTemplate9='';
        }else{
          console.log(this.checked1,this.checked2,this.checked3)
          if(this.checked1==false){
            this.postageTemplate1='';
          }
          if(this.checked2==false){
            this.postageTemplate2='';
          }
          if(this.checked3==false){
            this.postageTemplate3='';
          }
        }
      //普通寄递  选后面三个任意一个普通寄递都会被勾选
        if(this.checked1||this.checked2||this.checked3==true){
          this.checked7=true;
        }else{
          this.checked7=false;
        }
        if(this.checked1==false){
          this.postageTemplate1='';
        }else if(this.checked2==false){
          this.postageTemplate2='';
        }else if(this.checked3==false){
          this.postageTemplate3='';
        }

      },isChange8(oldValue){
        if(oldValue){
          this.checked7=false;
          this.checked9=false;
          this.checked1=false;
          this.checked2=false;
          this.checked3=false;
          this.checked10=false;
          this.checked11=false;
          this.checked12=false;
          this.postageTemplate1='';
          this.postageTemplate2='';
          this.postageTemplate3='';
          this.postageTemplate7='';
          this.postageTemplate8='';
          this.postageTemplate9='';
        }else{
          if(this.checked4==false){
            this.postageTemplate4='';
          }
          if(this.checked5==false){
            this.postageTemplate5='';
          }
          if(this.checked6==false){
            this.postageTemplate6='';
          }
        }
        //集中寄递  选后面三个任意一个集中寄递都会被勾选
        if(this.checked4||this.checked5||this.checked6==true){
          this.checked8=true;
        }else{
          this.checked8=false;
        }
        if(this.checked4==false){
          this.postageTemplate4='';
        }else if(this.checked5==false){
          this.postageTemplate5='';
        }else if(this.checked6==false){
          this.postageTemplate6='';
        }
      },isChange9(oldValue){
        if(oldValue){
          this.checked7=false;
          this.checked8=false;
          this.checked1=false;
          this.checked2=false;
          this.checked3=false;
          this.checked4=false;
          this.checked5=false;
          this.checked6=false;
          this.postageTemplate1='';
          this.postageTemplate2='';
          this.postageTemplate3='';
          this.postageTemplate4='';
          this.postageTemplate5='';
          this.postageTemplate6='';
        }else{
          if(this.checked10==false){
            this.postageTemplate7='';
          }
          if(this.checked11==false){
            this.postageTemplate8='';
          }
          if(this.checked12==false){
            this.postageTemplate9='';
          }
        }
        //分级寄递 选后面三个任意一个集中寄递都会被勾选
        if(this.checked10||this.checked11||this.checked12==true){
          this.checked9=true;
        }else{
          this.checked9=false;
        }
        if(this.checked10==false){
          this.postageTemplate7='';
        }else if(this.checked11==false){
          this.postageTemplate8='';
        }else if(this.checked12==false){
          this.postageTemplate9='';
        }
      },save(){
        this.gccSkuConsignment=[];
              //为防止只推送普通寄递和集中寄递
            if(this.checked7==true&&this.checked1==false&&this.checked2==false&&this.checked3==false){
              this.$message.error("请选择普通寄递方式");
              return false;
            }
            if(this.checked8==true&&this.checked4==false&&this.checked5==false&&this.checked6==false){
              this.$message.error("请选择集中寄递方式");
              return false;
            }
            if(this.checked9==true&&this.checked10==false&&this.checked11==false&&this.checked12==false){
              this.$message.error("请选择分级寄递方式");
              return false;
            }
        if(this.checked0==true){
          var obj={
            "dispatchModeCode": "",  //寄递方式代码 : 挂号信：1101， 邮政小包：1102， EMS：1103
            "dispatchModeName": "",   //寄递方式名称
            "dispatchType": "1",  //寄递类型:寄递类型:1：网点自提（自提）2：普通寄递（寄递）3：集中寄递（寄递）4：送货上门（保留）
            "dispatchTypeName":"网点自提",
            "isDefault": 0,   //是否是默认配送方式：0非默认，1默认
            "skuId": this.skuItem.skuId,
            "spuId": this.skuItem.spuId
          }
          this.gccSkuConsignment.push(obj);
          this.tempflag=true;
        }
        //防止只选择寄递不选择配送类型和配送方式
        if(this.checked0||this.checked7||this.checked8||this.checked9!==false){
          if(this.checked1==true){
            var obj={
              "dispatchModeCode": "1101",
              "dispatchModeName": "挂号信",
              "dispatchType": '2',
              "dispatchTypeName":"普通寄递", 
              "isDefault": 0,
              "postageTemplate":this.postageTemplate1,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate1==''||this.postageTemplate1==null){
              this.tempflag=false;
              this.$message.error("请选择普通寄递-挂号信-运费模板");
              return false;
            }
          }
          if(this.checked2==true){
            var obj={
              "dispatchModeCode": "1102",
              "dispatchModeName": "邮政小包",
              "dispatchType": '2',
              "dispatchTypeName":"普通寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate2,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate2==''||this.postageTemplate2==null){
              this.tempflag=false;
              this.$message.error("请选择普通寄递-邮政小包-运费模板");
              return false;
            }
          }
          if(this.checked3==true){
            var obj={
              "dispatchModeCode": "1103",
              "dispatchModeName": "EMS",
              "dispatchType": '2',
              "dispatchTypeName":"普通寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate3,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate3==''||this.postageTemplate3==null){
              this.tempflag=false;
              this.$message.error("请选择普通寄递-EMS-运费模板");
              return false;
            }
          }
          if(this.checked4==true){
            var obj={
              "dispatchModeCode": "1101",
              "dispatchModeName": "挂号信",
              "dispatchType": '3',
              "dispatchTypeName":"集中寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate4,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate4==''||this.postageTemplate4==null){
              this.tempflag=false;
              this.$message.error("请选择集中寄递-挂号信-运费模板");
              return false;
            }
          }
          if(this.checked5==true){
            var obj={
              "dispatchModeCode": "1102",
              "dispatchModeName": "邮政小包",
              "dispatchType": '3',
              "dispatchTypeName":"集中寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate5,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate5==''||this.postageTemplate5==null){
              this.tempflag=false;
              this.$message.error("请选择集中寄递-邮政小包-运费模板");
              return false;
            }
          }
          if(this.checked6==true){
            var obj={
              "dispatchModeCode": "1103",
              "dispatchModeName": "EMS",
              "dispatchType": '3',
              "dispatchTypeName":"集中寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate6,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate6==''||this.postageTemplate6==null){
              this.tempflag=false;
              this.$message.error("请选择集中寄递-EMS-运费模板");
              return false;
            }
          }
          if(this.checked10==true){
            var obj={
              "dispatchModeCode": "1101",
              "dispatchModeName": "挂号信",
              "dispatchType": '4',
              "dispatchTypeName":"分级寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate7,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate7==''||this.postageTemplate7==null){
              this.tempflag=false;
              this.$message.error("请选择分级寄递-挂号信-运费模板");
              return false;
            }
          }
          if(this.checked11==true){
            var obj={
              "dispatchModeCode": "1102",
              "dispatchModeName": "邮政小包",
              "dispatchType": '4',
              "dispatchTypeName":"分级寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate8,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate8==''||this.postageTemplate8==null){
              this.tempflag=false;
              this.$message.error("请选择分级寄递-邮政小包-运费模板");
              return false;
            }
          }
          if(this.checked12==true){
            var obj={
              "dispatchModeCode": "1103",
              "dispatchModeName": "EMS",
              "dispatchType": '4',
              "dispatchTypeName":"分级寄递",
              "isDefault": 0,
              "postageTemplate":this.postageTemplate9,//运费模板id
              "skuId":this.skuItem.skuId,
              "spuId":this.skuItem.spuId
            }
            this.gccSkuConsignment.push(obj)
            if(this.postageTemplate9==''||this.postageTemplate9==null){
              this.tempflag=false;
              this.$message.error("请选择分级寄递-EMS-运费模板");
              return false;
            }
          }
        this.tempflag=true;
        }else{
          this.tempflag=false;
          this.$message.error("请选择一种寄递方式");
          return false;
        }
        // else if(this.$route.query.isCollaboration=='1'&&this.gccSkuDispatchModes.length==0){
        //   this.tempflag=false;
        //   this.$message.error("协同商品未推送寄递方式");
        //   return false;
        // }
        let temp={
          "flag":this.tempflag,
          "gccSkuDispatchModes": this.gccSkuConsignment
        }
        return temp;
      },
      // 选中运费模板  查询运费模板详情
			  selectPostage:function(event){ 
			         // console.log(event)
			       if(event==''){
			            this.postageTempDetail={}   
			            this.$store.dispatch('postageTempDetail',this.postageTempDetail)  
			       }else{
                       this.postageDetail(event)
			       }
			      
         },
         initData:function(){
			 	let params = {
			 	       'pageNo':1,
			 	       'pageSize':100
			 	     }
			 	this.$axios.post(this.postageTemplateListUrl,params).then((res)=>{             
			 	    if(res.data.retCode=='1'){ //成功就是1
			 	        // console.log(res.data.data.items)
			 	        this.postageTemplateList=res.data.data.items
			 	        this.flag=true
			 	    }else{
			 	       this.$message.error(res.data.retMessage);
			 	    }
			 	})
			 }
    }
  }
</script>
<style>
.deliveryModule .el-form-item{
  width: 100%;
}
.deliveryModule .el-form-item__content{
   width: 100%;
   height: auto!important;
   line-height: auto!important;
}
.deliveryModule .el-checkbox__label{
  font-size: 12px;
}
.deliveryModule .consign-box{
  float:left;
  margin-top:5px;
}
.deliveryModule #row .el-col{
  margin-right: 10px
}
</style>
