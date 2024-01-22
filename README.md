串口发送模块

1.2模块设计与实现

| 名称    | 功能描述   |
| ------ | ------ |
| div_cnt |  产生波特率时钟|
| bps_cnt |对波特率时钟进行计数  |
| DR_LUT |查找表，以适用于不同波特率  |
| MUX10 | 根据 bps_cnt 的值来确定需要发送位 |
| MUX2 | 模块的使能信号 |

1.3波特率时钟生成模块设计
1.4数据输出模块设计
    通过对波特率始终进行计数，来确定发送的循环状态。
    //bps counter
    always@(posedge clk or posedge reset)
    if(reset) 
        bps_cnt <= 4'd0;
    else if(bps_cnt == 4'd11)
        bps_cnt <= 4'd0;
    else if(bps_clk)
        bps_cnt <= bps_cnt + 1'b1;
    else
        bps_cnt <= bps_cnt;
