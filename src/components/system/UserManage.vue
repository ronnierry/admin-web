<template>
    <div>
        <Row>
            <Col span="11">
                 用户名 : <Input prefix="ios-contact" v-model="name" placeholder="Enter name" style="width: auto" />
            </Col>
            <Col span="11">
                日期 : <DatePicker type="daterange" placement="bottom-end" placeholder="Select date" style="width: 200px"></DatePicker>
            </Col>
            <Col span="2">
                 搜索 :  <Button type="primary" shape="circle" icon="ios-search" @click='search'></Button>
            </Col>
        </Row>
        
        
        <div id="user">
            <Table :columns="columns1" :data="data1"></Table>
            <Page :total="total" :page-size='10' @on-change='onChange' show-sizer show-elevator show-total ></Page>
        </div>
    </div>
</template>
<script>
import { sumTow } from '../../common/common.js'
    export default {
        data () {
            return {
                columns1: [
                    {
                        title: 'Name',
                        key: 'name'
                    },
                    {
                        title: 'Age',
                        key: 'age'
                    },
                    {
                        title: 'Address',
                        key: 'address'
                    }
                ],
                data1: [
                    {
                        name: '胖鼠1号',
                        age: 18,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: '胖鼠2号',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: '胖鼠3号',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: '胖鼠4号',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ],
                name : "",
                total : 100
                
            }
        },
        methods: {
            search : function(){

                let con = [
                    {
                        name: 'John Brown',
                        age: 18,
                        address: 'New York No. 1 Lake Park',
                        date: '2016-10-03'
                    },
                    {
                        name: 'Jim Green',
                        age: 24,
                        address: 'London No. 1 Lake Park',
                        date: '2016-10-01'
                    },
                    {
                        name: 'Joe Black',
                        age: 30,
                        address: 'Sydney No. 1 Lake Park',
                        date: '2016-10-02'
                    },
                    {
                        name: 'Jon Snow',
                        age: 26,
                        address: 'Ottawa No. 2 Lake Park',
                        date: '2016-10-04'
                    }
                ]
                
                console.log("666")
                console.log(this.name)
                var sum = sumTow(1,2)
                console.log("sum :" + sum)

                if (this.name==''){
                    this.data1 = con;
                    
                }else{
                    this.data1 = []
                    con.forEach(
                        (x) => {
                            console.log(x.name)
                            if(x.name.indexOf(this.name) != -1){
                                this.data1.push(x)
                            }
                        }
                    )            
                }
                this.total = this.data1.length
            },
            onChange : function(x){
                console.log(x)
            }
        },
       
    }
</script>