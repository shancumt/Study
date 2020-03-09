```matlab
%*************************%
%******绘制正余弦波形******%
%*************************%
t = 0:2*pi/64:12*pi;
y1 = sin(t);
y2 = cos(t);
h_figure = figure('color','w');%创建一个背景为白色的画布
h_plot1 = plot(t,y1,'-.','linewidth',0.5,'color',[220,87,18]/255);
hold on
h_plot2 = plot(t,y2,'--','linewidth',0.5,'color','r');
box off    %删除边框
%***********设置图例**********%
%**http://blog.sina.com.cn/s/blog_49d955150101jyd9.html**%
%**https://blog.csdn.net/rookiew/article/details/51442347**%
h_legend1 = legend('\fontname{Times New Roman}sin\fontname{宋体}函数','\fontname{Times New Roman}cos\fontname{宋体}函数','location','northoutside');
legend boxoff   %删掉legend的边框
legend('boxoff')
legend('Orientation','horizon')     %legend横排
%***********设置figure的大小**********%
%**https://shancumt.github.io/Study/Matlab/matlab%E5%9B%BE%E5%BD%A2%E5%8F%A5%E6%9F%84.html**%
set (gcf,'units','centimeters','Position',[4,3,12.6,10.8]);    %设置画布的大小 
%***********删除图片周围的空白**********%
%** https://blog.csdn.net/shanchuan2012/article/details/53980288**%
set(gca,'looseInset',[0 0 0 0])
%***设置坐标轴的参数*****%
set(gca,'FontName','Times New Roman','FontSize',7.5,'position',[0.10,0.6265,0.865,0.3])     %设置坐标轴字体大小，字型
%*****设置坐标轴标签*****%
h_xlabel = xlabel('\fontname{华文中宋}采样点','FontSize',7.5);
h_xlabel = xlabel({'\fontname{华文中宋}采样点';'两行'},'FontSize',7.5);	%绘制两行标签
h_ylabel = ylabel('\fontname{华文中宋}值','fontsize',7.5);
%*******绘制箭头********%
%**https://www.ilovematlab.cn/thread-328986-1-1.html**%
annotation('textarrow',[0.71 0.79],...
[0.71 0.83],'string','sin(x)','linestyle','-','linewidth',1.5,'color',[0 0 1],'HeadStyle','cback3');

%********************%
%******绘制椭圆******%
%********************%
subplot(212)
sita=0:pi/20:2*pi;
x0=0;y0=0;
a=2;b=4;
fi=0;
plot(x0+a*cos(sita+fi),y0+b*sin(sita+fi));%fi为方位角，x0,y0为中心点坐标，a，b为长短轴；
%**使用latex对文本进行注释**%
%**https://blog.csdn.net/zd0303/article/details/7536967**%
%**https://zhidao.baidu.com/question/2016329392828714748.html**%
text(-1.9,0.34 ,'$$\leftarrow \frac{x}{2^2}+\frac{y}{4^2}=1$$','interpreter','latex')
%箭头起始点（0.71,0.18），箭头结束点（0.18,0.38），坐标值为figure的归一化坐标。
xticks([-2 -1.5 -1 0 1 2]);    %设置X坐标轴刻度数据点位置
% set(gca, 'YTick', [-15 -10 -5 0 5 10 15])    %设置X坐标轴刻度数据点位置
set(gca,'XTickLabel',{'-2','-1.5','-1','0','1','2'})    %设置X坐标轴刻度处显示的字符
% xticklabels(['-2','-1.5','-1','0','1','2']);
% axis([0,90,-20,20])    %设置坐标轴的显示范围
% set(gca,'YTickLabel',[]); %只显示y坐标轴刻度，不显示y坐标轴的值；
% set(gca,'XTickLabel',[]); %只显示x坐标轴刻度，不显示x坐标轴的值；
% set(gca,'ytick',[]); %y轴的坐标值和刻度均不显示；
% set(gca,'xtick',[]); %x轴的坐标值和刻度均不显示；
```



参考文献：

[MATLAB画图常用调整代码](http://blog.chinaunix.net/uid-11829250-id-3472528.html)

[MATLAB绘图属性操作](https://blog.csdn.net/healingwounds/article/details/78470954)