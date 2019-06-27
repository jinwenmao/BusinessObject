演练：在本地处理模式下将业务对象数据源与 ReportViewer Windows 窗体控件一起使用
https://docs.microsoft.com/zh-cn/previous-versions/ms251784(v=vs.140)#%E8%AF%B7%E5%8F%82%E8%A7%81

演练：在本地处理模式下将业务对象数据源与 ReportViewer Windows 窗体控件一起使用

    2015/07/31

本演练演示如何在 Microsoft Visual Studio Windows 窗体应用程序的报表中通过业务对象使用对象数据源。有关业务对象和对象数据源的更多信息，请参见Binding to Business Objects。

执行下列步骤将报表添加到 Windows 窗体应用程序项目中。对于此示例，您将使用 Microsoft Visual C# 创建应用程序。
创建新的 Windows 窗体应用程序项目

    在**“文件”菜单上，指向“新建”，然后选择“项目”**。

    在**“新建项目”对话框中的“已安装的模板”窗格中，选择“Visual C#”，然后选择“Windows 窗体应用程序”模板。根据 Visual Studio 中的启动设置，“C#”节点可能会显示在“其他语言”**下。

    键入项目的名称“BusinessObject”，并单击**“确定”**。

创建要用作数据源的业务对象

    从**“项目”菜单中选择“添加新项”**。

    在**“添加新项”对话框中，选择“类”，键入文件名“BusinessObjects.cs”**，然后单击“添加”。

    新文件将添加到项目并且在 Visual Studio 中自动打开。

    将 BusinessObjects.cs 的默认代码替换为以下代码：
    C# 

    using System;
    using System.Collections.Generic;

    // Define the Business Object "Product" with two public properties
    //    of simple datatypes.
    public class Product {
        private string m_name;
        private int m_price;

        public Product(string name, int price) {
            m_name = name;
            m_price = price;
        }

        public string Name {
            get {
                return m_name;
            }
        }

        public int Price {
            get {
                return m_price;
            }
        }
    }

    // Define Business Object "Merchant" that provides a 
    //    GetProducts method that returns a collection of 
    //    Product objects.

    public class Merchant {
        private List<Product> m_products;

        public Merchant() {
            m_products = new List<Product>();
            m_products.Add(new Product("Pen", 25));
            m_products.Add(new Product("Pencil", 30));
            m_products.Add(new Product("Notebook", 15));
        }

        public List<Product> GetProducts() {
            return m_products;
        }
    }

    从**“项目”菜单中，选择“生成解决方案”**。这将为对象创建一个程序集，您稍后会将此程序集用作报表的数据源。

使用报表向导向项目添加报表

    从**“项目”菜单中选择“添加新项”**。

    在**“添加新项”对话框中，选择“报表向导”。为报表键入名称，并单击“添加”**。

    这将启动报表向导中的数据源配置向导。

    在**“选择数据源类型”页上，选择“对象”，并单击“下一步”**。

    在**“选择数据对象”页中的“BusinessObject”下，展开类的层次结构，直到在列表中看到“产品”。选择“产品”，再单击“完成”**。

    现在已返回到“报表向导”。请注意，新数据源对象已添加到**“解决方案资源管理器”**中的项目中。

    在**“数据集属性”页中的“数据源”框中，确认选中“全局”**。

    在**“可用数据集”框中，确认选中“产品”**。

    单击**“下一步”**。

    在**“排列字段”**页中，执行以下操作：

        将**“名称”从“可用字段”拖到“行组”**框。

        将**“价格”从“可用字段”拖到“值”**框。

    单击两次**“下一步”，然后单击“完成”**。

    这将创建 .rdlc 文件并在报表设计器中将其打开。所创建的 tablix 会立即显示在设计图面中。

    保存 .rdlc 文件。

向报表中添加 ReportViewer 控件

    在解决方案资源管理器的“设计”视图中打开该 Windows 窗体。默认情况下，窗体名称为**“Form1.cs”**。

    在**“报表”组中，将“ReportViewer”图标从“工具箱”**拖到窗体上。

    在 ReportViewer 控件中，通过单击右上角的智能标记标志符号打开智能标记面板。

    在**“选择报表”**列表中，选择刚才设计的报表。默认情况下，名称为 Report1.rdlc。请注意，将为报表中使用的每个对象数据源相应自动创建名为 ProductBindingSource 的 BindingSource 对象。

    在打开的智能标记面板中，选择**“在父容器中停靠”**。

为 BindingSource 对象提供数据源实例

    在解决方案资源管理器中，右键单击**“Form1.cs”，然后选择“查看代码”**。

    在“Form1.cs”的分部类定义中，在构造函数前添加以下代码作为第一行。

// Instantiate the Merchant class.
private Merchant m_merchant = new Merchant();

在**“Form1_Load()”**方法中，在 RefreshReport 前添加下列代码作为第一行：

    // Bind the Product collection to the DataSource.
    this.ProductBindingSource.DataSource = m_merchant.GetProducts();

运行此应用程序

    按**“F5”**运行应用程序并查看报表。

请参见
参考

ReportViewer.Drillthrough

LocalReport.SubreportProcessing

ReportViewer.Drillthrough

LocalReport.SubreportProcessing
概念

使用“ReportViewer 任务”智能标记面板
其他资源

示例和演练

