###### 

#### 表单组件

> 表单组件通常在一个form 容器中使用，form 表单包含  一个个 form-item ,form-item 用于label 和   message展示控制 及 表单验证。表单组件：input 、inputnumber、radio 、checkbox、selector、cascader来做具体的展示及交互。如下是各个组件的使用说明



###### form - 表单容器

> 用于绑定form 对象，设置label宽度，对齐方式，绑定验证规则，绑定回调函数。

（1）基本使用


```
<template>
  <div>
    <SpForm :model="form" @doSubmit="submitForm" labelAlign="center">
        <SpFormItem prop="username" label="姓名">
            <SpInput v-model="form.username" placeholder="请输入姓名" size="small"></SpInput>
        </SpFormItem>
        <SpFormItem prop="phone" label="手机号">
            <SpInput v-model="form.phone" placeholder="请输入手机号" size="small"></SpInput>
        </SpFormItem>
        <SpFormItem prop="cascader" label="组件">
            <SpCascader :options="caseOptions" v-model="form.job" size="small"></SpCascader>
        </SpFormItem>
        <SpFormItem prop="phoneResult" label="电话跟进">
            <SpSelector v-model="form.phoneResult" label="电话跟进结果" :options="options" size="small"></SpSelector>
        </SpFormItem>

        <SpFormItem prop="time">
            <SpRadioGroup name="time" v-model="form.time" itemStyle="oneline">
                <SpRadio label="今天"></SpRadio>
                <SpRadio label="一周"></SpRadio>
                <SpRadio label="一月"></SpRadio>
            </SpRadioGroup>
        </SpFormItem>
        <SpButton size="small" type="primary" nativeType="submit">搜索</SpButton>
        <SpButton size="small" type="secondary" nativeType="reset">清空</SpButton>
    </SpForm>
  </div>
</template>
<script>
    export default{
        data(){
            return{
              labelType:"oneline",
              form:{
                username:'',
                phone:'',
                job:[],
                phoneResult:'',
                time:''
               }
            }
        }
    }
</script>

```
(2) form 参数列表


<html>
  <table>
      <tr>
            <th>参数</th>
            <th width="200">说明</th>
            <th>类型</th>
            <th>是否必填</th>
            <th>可选值</th>
            <th>默认值</th>
      </tr>
      <tr>
            <td>model</td>
            <td>绑定实体对象</td>
            <td>Object</td>
            <td>是</td>
            <td>-</td>
            <td>null</td>
      </tr>
       <tr>
            <td>labelWidth</td>
            <td>表单label的宽度</td>
            <td>String</td>
            <td>否</td>
            <td>-</td>
            <td>150px</td>
      </tr>
      <tr>
            <td>labelAlign</td>
            <td>表单label对齐方式</td>
            <td>String</td>
            <td>否</td>
            <td>left / right / center</td>
            <td>left</td>
      </tr>
       <tr>
            <td>rules</td>
            <td>绑定的验证规则，如果不需要验证，可不填</td>
            <td>Object</td>
            <td>否</td>
            <td>-</td>
            <td>-</td>
      </tr>
      <tr>
            <td>showMessage</td>
            <td></td>
            <td>Boolean</td>
            <td>否</td>
            <td>-</td>
            <td>true</td>
      </tr>
</table>
</html>

（3）form-item 参数列表

<html>
  <table>
      <tr>
            <th>参数</th>
            <th width="200">说明</th>
            <th>类型</th>
            <th>是否必填</th>
            <th>可选值</th>
            <th>默认值</th>
      </tr>
      <tr>
            <td>prop</td>
            <td>form-item唯一标识，与绑定属性名,验证规则属性名相同</td>
            <td>String</td>
            <td>是</td>
            <td>-</td>
            <td>null</td>
      </tr>
       <tr>
            <td>label</td>
            <td>label文字描述</td>
            <td>String</td>
            <td>是</td>
            <td>-</td>
            <td>null</td>
      </tr>
      <tr>
            <td>labelType</td>
            <td>label展示的位置,oneline和组件在一行展示，twoline各自独立一行</td>
            <td>String</td>
            <td>否</td>
            <td>oneline</td>
            <td>twoline</td>
      </tr>
       <tr>
            <td>required</td>
            <td>是否为必填项，设置为true,则在label前面显示红色星号</td>
            <td>Boolean</td>
            <td>否</td>
            <td>true / false</td>
            <td>false</td>
      </tr>
      <tr>
            <td>maskType</td>
            <td>出错文案位置, 默认右侧，可设置为bottom 下边</td>
            <td>String</td>
            <td>否</td>
            <td>bottom / right</td>
            <td>right</td>
      </tr>
      <tr>
            <td>customMask</td>
            <td>自定义出错文案</td>
            <td>String</td>
            <td>否</td>
            <td>-</td>
            <td>-</td>
      </tr>
</table>
</html>

方法

<html>
  <table>
      <tr>
            <th>参数</th>
            <th width="200">说明</th>
            <th>参数</th>
            <th>返回值</th>
      </tr>
      <tr>
            <td>setMask</td>
            <td>显示出错提示</td>
            <td>-</td>
            <td>-</td>
      </tr>
      <tr>
            <td>hideMask</td>
            <td>隐藏出错提示</td>
            <td>-</td>
            <td>-</td>
      </tr>
</table>
</html>


###### 验证规则说明

> 按如下规则进行配置，name 为需要验证的属性名，即form-item 的prop属性值 。包含12种 type 类型验证规则，其中pattern reg 可进行正则表达式验证，message 为验证提示语，trigger 为验证触发时机，可选值：blur 失去焦点验证，change 数据变化时验证


```
  rules:  {
              name: [
                { type:'required',message: '请输入活动名称', trigger: 'blur' },
                { type:'valueRange', min:3, max:10, message:'最小不小于3,最大不大于10', trigger: 'blur' },
                { type:'lengthRange', min:3, max:10, message:'长度在 3 到 10 个字符', trigger: 'blur' },
                { type:'url',message:'请输入正确网址地址', trigger: 'blur'},
                { type:'min',min:3,message:'最小值不于3', trigger: 'blur'},
                { type:'max',max:10,message:'最大值不于10', trigger: 'blur'},
                { type:'minlength',min:3,message:'请输入最少3个字符', trigger: 'blur'},
                { type:'maxlength',max:10,message:'请输入最多10个字符', trigger: 'blur'},
                { type:'phone',message:'请输入正确的手机号', trigger: 'blur'},
                { type:'email',message:'请输入正确的邮箱地址', trigger: 'blur'},
                { type:'number',message:'请输入数字', trigger: 'blur'},
                { type:'pattern',reg:'^[#$%^&*]$/g',message:'请勿输入非法字符', trigger: 'blur'}
              ]
          }
```

