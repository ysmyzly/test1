<template>
    <div class="hotelMana">
        <nav>
            <div>收入明细</div>
            <div>合同截止至：2025-10-12
                <span class="distance">剩余KEY数量：102</span> 预计使用时间：34天
            </div>
        </nav>
        <div class="essential">
            <div class="searchContent">
                编号：
                <el-input size="small"></el-input>
                <span class="leftMargin">销售产品：</span>
                <el-select v-model="product" placeholder="请选择" size="small">
                    <el-option v-for="item in products" :key="item.value" :label="item.label" :value="item.value">
                    </el-option>
                </el-select>
                <span class="leftMargin">产品类型：</span>
                <el-select v-model="productType" placeholder="请选择" size="small">
                    <el-option v-for="item in productTypes" :key="item.value" :label="item.label" :value="item.value">
                    </el-option>
                </el-select>
                <span class="leftMargin">产品名称：</span>
                <el-input size="small"></el-input><br><br>
                <span>分销时间：</span>
                <el-date-picker size="small" v-model="value1" type="daterange" range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期">
                </el-date-picker>
                <el-button type="primary" size="small">搜索</el-button>
                <el-button plain type="primary" size="small">重置</el-button>
                <el-button plain type="primary" size="small">导出execl</el-button>
            </div>
            <div>
                <div class="totalSales">销售总额：50</div>
                <el-table border align="center" :data="tableData" style="width: 100%" :default-sort="{prop: 'date', order: 'descending'}">
                    <el-table-column prop="date" label="编号" align="center" sortable>
                    </el-table-column>
                    <el-table-column prop="name" align="center" label="收入" sortable>
                    </el-table-column>
                    <el-table-column prop="name" align="center" label="销售产品">
                    </el-table-column>
                    <el-table-column prop="name" align="center" label="产品类型">
                    </el-table-column>
                    <el-table-column prop="name" align="center" label="产品名称">
                    </el-table-column>
                    <el-table-column prop="name" align="center" label="订单总价">
                    </el-table-column>
                    <el-table-column label="店内分销模板" align="center">
                        <el-table-column prop="name" label="店长" align="center">
                        </el-table-column>
                        <el-table-column prop="name" label="店员" align="center">
                        </el-table-column>
                    </el-table-column>
                    <el-table-column prop="name" align="center" label="分销时间">
                    </el-table-column>
                    <el-table-column label="操作" align="center" width="120">
                        <template slot-scope="scope">
                            <el-button size="mini" icon="el-icon-edit-outline" @click="handleEdit(scope.$index, scope.row)">查看详情</el-button>

                        </template>
                    </el-table-column>
                </el-table>
            </div>
            <div class="paging">
                <el-pagination @size-change="handleSizeChange" @current-change="handleCurrentChange" :current-page="currentPage4" :page-sizes="[100, 200, 300, 400]" :page-size="100" layout="total, sizes, prev, pager, next, jumper" :total="400">
                </el-pagination>
            </div>
        </div>

    </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  //   name: "HotelMana",
  // components: {
  //   HelloWorld
  // }
  data() {
    return {
      value1: null,
      tableData: [
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-08",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-06",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-07",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        }
      ],
      multipleSelection: [],
      currentPage4: 4,
      product: "全部",
      products: [
        {
          value: "选项1",
          label: "全部"
        },
        {
          value: "选项2",
          label: "影视卡"
        },
        {
          value: "选项3",
          label: "投影key"
        }
      ],
      productType: "全部",
      productTypes: [
        {
          value: "选项1",
          label: "全部"
        },
        {
          value: "选项2",
          label: "日卡"
        },
        {
          value: "选项3",
          label: "周卡"
        },
        {
          value: "选项4",
          label: "月卡"
        },
        {
          value: "选项5",
          label: "季卡"
        },
        {
          value: "选项6",
          label: "半年卡"
        },
        {
          value: "选项7",
          label: "年卡"
        },
        {
          value: "选项8",
          label: "投影key"
        }
      ]
    };
  },
  methods: {
    handleEdit(index, row) {
      console.log(index, row);
    },
    handleDelete(index, row) {
      console.log(index, row);
    },
    handleSelectionChange(val) {
      this.multipleSelection = val;
    },
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    }
  }
};
</script>

<style lang='scss'  scoped>
$color: #8ad151;
$sizeColor: #fff;
.hotelMana {
  nav {
    background-color: $color;
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    color: $sizeColor;
    .distance {
      padding: 0 20px;
    }
  }
  .essential {
    color: #333;
    font-size: 16px;
    // font-weight: bold;
    padding: 20px 0 0 20px;
  }
  .el-input {
    width: auto;
  }
  .searchContent {
    padding-bottom: 20px;
    .leftMargin {
      padding-left: 10px;
    }
    .el-button--small,
    .el-button--small.is-round {
      margin-left: 10px;
    }
  }
  .paging {
    text-align: center;
    padding-top: 10px;
  }
  .totalSales{
      font-size: 20px;
      padding-bottom: 10px;
  }
}
</style>


