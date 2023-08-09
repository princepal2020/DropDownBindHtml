# DropDownBindHtml
html dropdown 


html code --------------------------

<ul>


  
  <li class="dropdown">
        <a href="#" id="ddlItems" runat="server">
            <span>Services</span> <i class="bi bi-chevron-down"></i>
        </a>
        <ul id="serviceList" runat="server"></ul>
    </li>
</ul>

C# Code ========================================

protected void Page_Load(object sender, EventArgs e)
{
    if (!IsPostBack)
    {
        // Fetch data from the database (replace this with your data retrieval logic)
        DataTable servicesTable = GetServicesDataFromDatabase();

        // Generate list items for the "Services" dropdown
        foreach (DataRow row in servicesTable.Rows)
        {
            string serviceName = row["ServiceName"].ToString();
            string serviceUrl = row["ServiceUrl"].ToString();

            HtmlGenericControl li = new HtmlGenericControl("li");
            HtmlAnchor a = new HtmlAnchor();
            a.HRef = serviceUrl;
            a.InnerText = serviceName;

            li.Controls.Add(a);
            serviceList.Controls.Add(li);
        }
    }
}
