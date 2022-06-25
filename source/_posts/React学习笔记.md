---
thumbnail: 'https://picsum.photos/1280/720?random=1 #111'
title: React学习笔记
date: 2021-11-14 13:42:44
tags: 
- 🔥前端
- 🚀框架
- 📔笔记
---
**用于构建用户界面的 JavaScript 库**

state是当前组件的状态

props是获取父组件的state值

class类里，this指向当前类内的内容。例如this.state指向当前类的state状态；this.function指向当前类的方法。

**AntDesignPro**

使用Ant Design pro脚手架官网来搭建项目，其中最重要的三个文件夹，services、models、mock、pages

- sevices：数据接口

- models：数据处理

- mock：模拟数据

- pages：页面

pages触发models中的方法来处理数据，若为异步操作在models中需要调用services中的数据接口方法，在后台未写完时可以通过mock中的模拟数据来调试

具体来说，也即是使用dva时，**数据流向或者说触发流程为：**在pages中的jsx文件中通过dispatch触发models中的js文件中的effects或者reducers中的方法，其中effects中的方法是异步操作，通过yield call(调用接口函数方法名)调用从services中js文件引入的定义好的调用接口方法，然后通过yield put({type: 'reduceres中的方法'})；来触发 reducers中的方法来修改state。

**组件生命周期**

componentWillMount 在渲染前调用,在客户端也在服务端。

componentDidMount : 在第一次渲染后调用，只在客户端。之后组件已经生成了对应的DOM结构，可以通过this.getDOMNode()来进行访问。 如果你想和其他JavaScript框架一起使用，可以在这个方法中调用setTimeout, setInterval或者发送AJAX请求等操作(防止异步操作阻塞UI)。

componentWillReceiveProps 在组件接收到一个新的 prop (更新后)时被调用。这个方法在初始化render时不会被调用。

getDerivedStateFromProps componentWillReceiveProps的替换方案。React相当于把componentWillReceiveProps拆分成getDerivedStateFromProps和componentDidUpdate。

shouldComponentUpdate 返回一个布尔值。在组件接收到新的props或者state时被调用。在初始化时或者使用forceUpdate时不被调用。 

可以在你确认不需要更新组件时使用。

componentWillUpdate在组件接收到新的props或者state但还没有render时被调用。在初始化时不会被调用。

componentDidUpdate 在组件完成更新后立即调用。在初始化时不会被调用。

componentWillUnmount在组件从 DOM 中移除之前立刻被调用。

**Hook**

在这里，useState 就是一个 Hook （等下我们会讲到这是什么意思）。通过在函数组件里调用它来给组件添加一些内部 state。React 会在重复渲染时保留这个 state。useState 会返回一对值：当前状态和一个让你更新它的函数，你可以在事件处理函数中或其他一些地方调用这个函数。它类似 class 组件的 this.setState，但是它不会把新的 state 和旧的 state 进行合并。

```javascript
function DetailQuery(props) {
    const { clickDetailQueryBtn, clickDetailResetBtn } = props;
    const [statu, setStatu] = useState({ getstatu: '全部' });
    const updateState = partialState =>
        setStatu(oldState => ({
            ...oldState,
            ...partialState
        }));
    
    return (
        <Layout>
            <Row
                style={{background: 'white', paddingTop: 20, paddingRight: 20, paddingBottom: 20}}
            >

                <Col span={6} className={styles.formItemClass}>
                    状态：
                    <Select 
                    // defaultValue="全部" 
                    style={{ width: 120 }} 
                    value={statu.getstatu}
                    onChange={e => {
                        updateState({ getstatu: e });} }
                    >
                        <Select.Option value="全部">全部</Select.Option>
                        <Select.Option value="待上报">待上报</Select.Option>
                        <Select.Option value="待审核">待审核</Select.Option>
                        <Select.Option value="已通过">已通过</Select.Option>
                        <Select.Option value="未通过">未通过</Select.Option>
                    </Select>
                </Col>
                <Col push={1} span={6}>
                    <Button
                        type="primary"
                        style={{marginRight: 7}}
                        onClick={() => {
                            clickDetailQueryBtn(statu);
                        }}
                    >
                        查询
                    </Button>
                    <Button
                        onClick={() => {
                            clickDetailResetBtn('');
                        }}
                        // onClick={this.props.clickDetailResetBtn}
                    >
                        重置
                    </Button>
                </Col>
            </Row>
        </Layout>
    );
}

```



**Router**

```javascript
// 审核和重新审核
export async function toExamineReport(params) {
    return request(Api.toExamineReport, { 
        method: 'POST' ,
        body: {
            ...params
        }
    })
}
// 查看上报记录
export async function getMyCorrectionReportQueryRecord(params) {
    return request(Api.getMyCorrectionReportQueryRecord + `?${stringify(params)}`, { 
        method: 'GET' ,
        // body: {
        //     ...params
        // }
    })
}
// 批量下载整改报告附件
export async function onPatchExport(params) {
    return request(Api.onPatchExport + `?${stringify(params)}`, { 
        method: 'GET' ,
        responseType: 'blob', // 下载文件
        // body: {
        //     ...params
        // }
    })
}
```

**react-devtools**

> × Install fail! Error: Unsupported URL Type: link:./scripts/eslint-rules

安装出错，需要把3个文件中的link改成file

![react_1](https://gitee.com/feng-lekai/blog-image/raw/master/img/react_1.jpg)

```json
link:./scripts/eslint-rules // 改前
file:./scripts/eslint-rules // 改后
```

安装教程

> https://blog.csdn.net/one_girl/article/details/80916232

**TypeError: Cannot read property 'split' of null**

str.split('.') 

变成

(str || "").split('.')

不报错啦

**routerRedux路由跳转**

```javascript
import router from 'umi/router';
import { routerRedux } from 'dva/router';

    this.props.dispatch(routerRedux.push({ 
      pathname : '/partyBuildingDebriefing/debriefingMeeting/meetingStaffManagement', 
      record:{
        detailVisibel: true, 
        detailProps: {
          title: '编辑述职会议及人员信息'},
        id: this.props.id
      } 
    }))
```

**Antd Table 合并某列单元格方法**

须传输出值text，和索引值index

```javascript
  // 合并单元格操作
  threeCell = (text, index) => {
    // 在render中所有的合并都仅仅相对所有的name这一列来说，index从0开始计算
    const obj = {
        children: index+1,
        props: {}
    };
    // 3个单元格取余
    let i = index%3;
    // index=0：相对name这一列，合并3列单元格
    if (i === 0) {
        obj.props.rowSpan = 3;
    }
    // 合并单元格后，则第1行渲染，第2，3行不渲染
    if (i > 0 && i <3) {
        obj.props.rowSpan = 0;
    }
    return obj
  }
```

**Input组件onChange事件获取value值**

```javascript
onChange = e => {
    const value = e.target.value;
    console.log(value);
}
```

**表单获取用户输入基本格式**

```jsx
<FormItem label='颁奖日期'>
 {form.getFieldDecorator('字段名', {
   initialValue: '默认值',
   rules: [{ message: '规则字段', }]
 })(<Input placeholder='页面渲染输入框'/>)}
</FormItem>
```

**重置表单验证保留输入值**

```js
// 重置表单tenderStatus属性的值以及表单验证提示（值会变成initialValue的值）
this.props.form.resetFields(['tenderStatus']);
// 将我们重置之前储存好的属性值，给联动表单的属性重新赋值，否则会变成initialValue的值
this.props.form.setFieldsValue({ tenderStatus: status });
```

**Antd中DatePicker组件在3.x及以下版本**

在使用mode属性API后选择日期没有反应，需要使用onPanelChange属性和onOpenChange属性改变open属性。

disabledDate属性没有效果，无法禁用相应年份，月份，只能禁用日期。可以在选择年份时判断当前日期与预期日期符不符合用message反馈给用户。

**Antd 给TableCell 添加key属性方法**

```js
  // 自动生成key
  generateRandomId = (length) => {// length是你的id的长度，可自定义
    return Math.random().toString(36).substr(3,length);
  }
```

**Hook 是 React 16.8 的新增特性。它可以让你在不编写 class 的情况下使用 state 以及其他的 React 特性**

```jsx
import React, { useState, useEffect } from 'react';
function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:  
  useEffect(() => {    // Update the document title using the browser API    document.title = `You clicked ${count} times`;  });
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

useState: 对应class中state,比其更加强大：对应变量自带方法setState解决复杂的逻辑问题。

useEffect:对应class中ComponentDidMount初始化渲染，属于副作用操作。