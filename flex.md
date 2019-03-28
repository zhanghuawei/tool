#### 弹性盒子属性设置：
            justify-content: center;垂直居中
            flex-direction: column;
            align-items: center;水平居中
            display: flex;
	          flex-direction:row;
            flex-wrap:wrap;
            flex-flow:row wrap;/*上面两属性的复合写法*/
            justify-content: space-around; /*首尾有间隙,并且间隙是盒子与盒子之间距离的一半*/
            align-items: flex-start;
            align-content: center; /*堆叠盒子的排列方式*/
            flex-grow: 0;/*设置扩展比例 ,默认的值是0*/
            flex-shrink: 1;/*设置收缩比例,默认值的值1*/
            flex-basis: 100px;/*基准值*/
	          align-items	 主轴原点方向对齐
            flex-end		主轴延伸方向对齐
            space-between   等间距排列，首尾不留白
            space-around	等间距排列，首尾留白
