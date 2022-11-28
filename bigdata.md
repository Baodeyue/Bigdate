
from datascience import *
import matplotlib.pyplot as plt

matplotlib inline 

def extract_rank(data,name):
   temp=data.where(‘名字’，are.equal_to(name)).column(11).item(0)
   return temp


data1=Table.read_table(‘./bigdata_test/20211105-utf-8.csv’)
data2=Table.read_table(‘./bigdata_test/20211106-utf-8.csv’)
data3=Table.read_table(‘./bigdata_test/20211107-utf-8.csv’)
data4=Table.read_table(‘./bigdata_test/20211108-utf-8.csv’)
data5=Table.read_table(‘./bigdata_test/20211109-utf-8.csv’)
data6=Table.read_table(‘./bigdata_test/20211109-1-utf-8.csv’)
data7=Table.read_table(‘./bigdata_test/202111010-utf-8.csv’)

name=’周靖珊’

rank1=extract_rank(data1,name)
rank2=extract_rank(data2,name)
rank3=extract_rank(data3,name)
rank4=extract_rank(data4,name)
rank5=extract_rank(data5,name)
rank6=extract_rank(data6,name)
rank7=extract_rank(data7,name)

rank_array=make_array(rank1,rank2,rank3,rank4,rank5,rank6,rank7)

results=Table().with_colums(‘考试序号’,make_array(1,2,3,4,5,6,7),’姓名’,rank_array)
results

plt.plot(make_array(1,2,3,4,5,6,7),rank_array,’o--’,label=name)

plt.xlabel(‘历次考试’)
plt.ylabel(‘年级RANK’)

plt.axis([0,10,650,150])
plt.legend(loc=’upper right’)

plt.rcParams[‘font.sans-serif’]=[‘Microsoft YaHei’]

plt.grid()
plt.show()