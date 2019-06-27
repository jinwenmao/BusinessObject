�������ڱ��ش���ģʽ�½�ҵ���������Դ�� ReportViewer Windows ����ؼ�һ��ʹ��
https://docs.microsoft.com/zh-cn/previous-versions/ms251784(v=vs.140)#%E8%AF%B7%E5%8F%82%E8%A7%81

�������ڱ��ش���ģʽ�½�ҵ���������Դ�� ReportViewer Windows ����ؼ�һ��ʹ��

    2015/07/31

��������ʾ����� Microsoft Visual Studio Windows ����Ӧ�ó���ı�����ͨ��ҵ�����ʹ�ö�������Դ���й�ҵ�����Ͷ�������Դ�ĸ�����Ϣ����μ�Binding to Business Objects��

ִ�����в��轫������ӵ� Windows ����Ӧ�ó�����Ŀ�С����ڴ�ʾ��������ʹ�� Microsoft Visual C# ����Ӧ�ó���
�����µ� Windows ����Ӧ�ó�����Ŀ

    ��**���ļ����˵��ϣ�ָ���½�����Ȼ��ѡ����Ŀ��**��

    ��**���½���Ŀ���Ի����еġ��Ѱ�װ��ģ�塱�����У�ѡ��Visual C#����Ȼ��ѡ��Windows ����Ӧ�ó���ģ�塣���� Visual Studio �е��������ã���C#���ڵ���ܻ���ʾ�ڡ��������ԡ�**�¡�

    ������Ŀ�����ơ�BusinessObject����������**��ȷ����**��

����Ҫ��������Դ��ҵ�����

    ��**����Ŀ���˵���ѡ��������**��

    ��**���������Ի����У�ѡ���ࡱ�������ļ�����BusinessObjects.cs��**��Ȼ�󵥻�����ӡ���

    ���ļ�����ӵ���Ŀ������ Visual Studio ���Զ��򿪡�

    �� BusinessObjects.cs ��Ĭ�ϴ����滻Ϊ���´��룺
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

    ��**����Ŀ���˵��У�ѡ�����ɽ��������**���⽫Ϊ���󴴽�һ�����򼯣����Ժ�Ὣ�˳����������������Դ��

ʹ�ñ���������Ŀ��ӱ���

    ��**����Ŀ���˵���ѡ��������**��

    ��**���������Ի����У�ѡ�񡰱����򵼡���Ϊ����������ƣ�����������ӡ�**��

    �⽫�����������е�����Դ�����򵼡�

    ��**��ѡ������Դ���͡�ҳ�ϣ�ѡ�񡰶��󡱣�����������һ����**��

    ��**��ѡ�����ݶ���ҳ�еġ�BusinessObject���£�չ����Ĳ�νṹ��ֱ�����б��п�������Ʒ����ѡ�񡰲�Ʒ�����ٵ�������ɡ�**��

    �����ѷ��ص��������򵼡�����ע�⣬������Դ��������ӵ�**�����������Դ��������**�е���Ŀ�С�

    ��**�����ݼ����ԡ�ҳ�еġ�����Դ�����У�ȷ��ѡ�С�ȫ�֡�**��

    ��**���������ݼ������У�ȷ��ѡ�С���Ʒ��**��

    ����**����һ����**��

    ��**�������ֶΡ�**ҳ�У�ִ�����²�����

        ��**�����ơ��ӡ������ֶΡ��ϵ������顱**��

        ��**���۸񡱴ӡ������ֶΡ��ϵ���ֵ��**��

    ��������**����һ������Ȼ�󵥻�����ɡ�**��

    �⽫���� .rdlc �ļ����ڱ���������н���򿪡��������� tablix ��������ʾ�����ͼ���С�

    ���� .rdlc �ļ���

�򱨱������ ReportViewer �ؼ�

    �ڽ��������Դ�������ġ���ơ���ͼ�д򿪸� Windows ���塣Ĭ������£���������Ϊ**��Form1.cs��**��

    ��**���������У�����ReportViewer��ͼ��ӡ������䡱**�ϵ������ϡ�

    �� ReportViewer �ؼ��У�ͨ���������Ͻǵ����ܱ�Ǳ�־���Ŵ����ܱ����塣

    ��**��ѡ�񱨱�**�б��У�ѡ��ղ���Ƶı���Ĭ������£�����Ϊ Report1.rdlc����ע�⣬��Ϊ������ʹ�õ�ÿ����������Դ��Ӧ�Զ�������Ϊ ProductBindingSource �� BindingSource ����

    �ڴ򿪵����ܱ������У�ѡ��**���ڸ�������ͣ����**��

Ϊ BindingSource �����ṩ����Դʵ��

    �ڽ��������Դ�������У��Ҽ�����**��Form1.cs����Ȼ��ѡ�񡰲鿴���롱**��

    �ڡ�Form1.cs���ķֲ��ඨ���У��ڹ��캯��ǰ������´�����Ϊ��һ�С�

// Instantiate the Merchant class.
private Merchant m_merchant = new Merchant();

��**��Form1_Load()��**�����У��� RefreshReport ǰ������д�����Ϊ��һ�У�

    // Bind the Product collection to the DataSource.
    this.ProductBindingSource.DataSource = m_merchant.GetProducts();

���д�Ӧ�ó���

    ��**��F5��**����Ӧ�ó��򲢲鿴����

��μ�
�ο�

ReportViewer.Drillthrough

LocalReport.SubreportProcessing

ReportViewer.Drillthrough

LocalReport.SubreportProcessing
����

ʹ�á�ReportViewer �������ܱ�����
������Դ

ʾ��������

