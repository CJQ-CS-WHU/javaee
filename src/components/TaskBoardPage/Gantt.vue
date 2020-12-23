<template>
  <el-card class ='card'> 
       <div class="header">
        <div class="left-header">
            <div>
                <el-dropdown @command="handleCommand1">
                    <span class="el-dropdown-link">
                      选择视图<i class="el-icon-arrow-down el-icon--right"></i>
                    </span>
                    <el-dropdown-menu slot="dropdown">
                      <el-dropdown-item command="board" style = "font-size: 18px">看板视图</el-dropdown-item>
                      <el-dropdown-item command="gantt" style = "font-size: 18px" divided>甘特图</el-dropdown-item>
                    </el-dropdown-menu>
                  </el-dropdown>
            </div>          
        </div>
    </div>
    
    <div class="wl-gantt-demo">
      <wlGantt
        :data="taskData"
        use-real-time
        default-expand-all
        date-type="yearAndMonth"
        :start-date="iterationBeginTime"
        :end-date="iterationEndTime"
        autoGanttDateType: Ture
        
      ></wlGantt>
    </div>
  </el-card>
</template>

<script>
import {mapState,mapGetters} from 'Vuex'
export default {
  name: "HelloWorld",
  data() {
    return {
      myArray:[],
      myArrayHere:[],
      taskData:[{
                id: 1,
                name: '任务一',
                startDate: '2020-02-02',
                endDate: '2020-09-05',
                realStartDate: '-',
                realEndDate:'-',
              },
              {id: 2,
                name: '任务二',
                startDate: '2020-05-02',
                endDate: '2021-03-05',
                realStartDate: "-",
                realEndDate: "-",
              },
               {id: 8,
                name: '任务八',
                startDate: '2020-01-07',
                endDate: '2021-04-05',
                realStartDate: "-",
                realEndDate: "-",
              },
               {id: 4,
                name: '任务四',
                startDate: '2020-08-02',
                endDate: '2021-02-05',
                realStartDate: "-",
                realEndDate: "-",
              },
               {id: 5,
                name: '任务五',
                startDate: '2020-02-02',
                endDate: '2021-05-05',
                realStartDate: "-",
                realEndDate: "-",
              },
              {id: 7,
                name: '任务七',
                startDate: '2020-08-02',
                endDate: '2021-10-05',
                realStartDate: "-",
                realEndDate: "-",
              },
               {id: 9,
                name: '任务九',
                startDate: '2020-04-02',
                endDate: '2020-06-05',
                realStartDate: "-",
                realEndDate: "-",
              },
               {id: 6,
                name: '任务六(已完成)',
                startDate: '2020-06-02',
                endDate: '2021-10-05',
                realStartDate: "-",
                realEndDate: "-",
              },
               {id: 3,
                name: '任务三(已完成)',
                startDate: '2020-03-15',
                endDate: '2020-09-05',
                realStartDate: "-",
                realEndDate: "-",
              }],
      iterationBeginTime: "2020-01-02",
      iterationEndTime:"2021-12-06"
    }
  },
   computed:{
        ...mapState('login',['userInfo']),  
    ...mapGetters(['currentProject'])
   },
  // mounted () {
  //   this.$axios
  //   .get('/api/userNameForAll?userName='+'张俊杰4')
  //        .then(response => {
  //             //console.log(response.data.data)            
  //         let project = response.data.data.filter(a=>a.teamProjectId == 2)
  //         let iteration = project[0].iterationVOs.filter(function(b){
  //             return b.iterationState=="执行中"
  //         })
  //       // console.log( iteration[0])
  //         this.myArray = iteration[0].taskVOs
  //         this.iterationBeginTime=iteration[0].iterationBeginTime
  //         this.iterationEndTime=iteration[0].iterationEndTime
  //         for (let i = 0; i < this.myArray.length; i++) { 
  //             if(this.myArray[i].taskState!=='已完成'){this.myArrayHere.push(this.myArray[i])}
  //           }
  //           console.log(this.myArrayHere)
  //          for (let i = 0; i < this.myArray.length; i++) { 
  //             if(this.myArray[i].taskState=='已完成'){
  //               this.myArray[i].taskRemark = this.myArray[i].taskRemark+"（已完成）"
  //               this.myArrayHere.push(this.myArray[i])}
  //           }
            
          
  //         for (let i = 0; i < this.myArrayHere.length; i++) {
         
  //           this.taskData.push(
  //             {
  //               id: this.myArrayHere[i].taskId,
  //               name: this.myArrayHere[i].taskRemark,
  //               startDate: this.myArrayHere[i].taskBeginTime.slice(0,10),
  //               endDate: this.myArrayHere[i].taskEndTime.slice(0,10),
  //               realStartDate: "-",
  //               realEndDate: "-",
  //             }
  //           )
  //         }
  //          // console.log(this.myArray[0].taskEndTime.slice(0,10))
  //       //console.log( this.myArray)
  //         //console.log( this.myArray1)
  //       })
  //       .catch(function (error) {
  //       console.log(error)
        
  //     })
  //    },
  methods: {
    /**
     * 时间发生更改
     * row: Object 当前行数据c
     */
    // timeChange(row) {
    //   console.log("时间修改:", row);
      
    //    this.$axios.put('/api/task',{"taskId":row.id,"taskBeginTime":row.startDate+" 12:12" , "taskEndTime":row.endDate+" 12:12"}).then((response) =>{
    //          console.log(response)})
    // },
    handleCommand1(command){
          switch(command){
              case 'board':
                  this.$router.push('/TaskBoard')
                    break;
              case 'gantt':
                  this.$router.push('/gantt')
                    break;
          }
    }
  }
}
</script>

<style scoped>
.header{
        width: 1300px;
        margin: 5px auto;
        height: 40px;
        /* border: 1px solid rgb(29, 10, 46); */
    }
.left-header{
        width: 240px;
        height: 40px;
        /* border: 6px solid green; */
        float: left;
    }
</style>