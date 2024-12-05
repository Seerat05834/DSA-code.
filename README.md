#include<iostream>
#include<string>
#include <queue>
#include <functional>  
const int max_size = 100;  // Choose an appropriate maximum size for your array
using namespace std;
class Login {
private:
    string username;
    string password;
public:
    Login(const string& uname = "", const string& pword = "") : username(uname), password(pword) {}
   
    string getUsername() const {
        return username;
    }
   
    string getPassword() const {
        return password;
    }
   
};
class supplier {
public:
    char c1;
    string sname[4];
    int sid[4];
    string scompany[4];
    string sphn[4];
    string semail[4];
    void sdata() {
        for (int i = 0; i < 4; i++) {
            cout << "Enter supplier name:";
            cin >> sname[i];
            cout << "Enter supplier id:";
            cin >> sid[i];
            cout << "Enter supplier company:";
            cin >> scompany[i];
            cout << "Enter supplier Phn no:";
            cin >> sphn[i];
            cout << "Enter supplier e-mail:";
            cin >> semail[i];
        HIJ4:
            cout << "Do you want to enter more?(Y/y or N/n):";
            cin >> c1;
            if (c1 == 'Y' || c1 == 'y') {
                continue;
            }
            else if (c1 == 'n' || c1 == 'N') {
                //system("cls");
                break;
            }
            else {
                cout << "Invalid input.\nKindly enter Again." << endl;
                goto HIJ4;
            }

        }

            system("cls");
            cout << "\t\t\tDATA DISPLAY" << endl;
            for (int j = 0; j < 4;j++) {
               if(sname[j].empty()) {
                   break;
                }
               else {
                   
                   cout << "SUPPLIER NAME:" << sname[j] << endl;
                   cout << "SUPPLIER ID:" << sid[j] << endl;
                   cout << "SUPPLIER COMPANY:" << scompany[j] << endl;
                   cout << "SUPPLIER PHN-NO:" << sphn[j] << endl;
                   cout << "SUPPLIER Email:" << semail[j] << endl;
                   cout << "\t\t\t" << endl;
               }
            }
                }
};
class Medicine
{
public:
    string tablet[20];
    string syrup[20];
    int quantityTab[20];
    int quantitySrp[20];
    int syrupExp[20];
    int tabletExp[20];
    int totalTab;
    int totalSrp;
    int counter1 = 0;
    int counter2 = 0;
    int value;
    void addData(string tab[4], string srp[4], int qtySrp[4], int qtyTab[4], int srpExp[4], int tabExp[4], int ttlSrp, int ttlTab)
    {
        for (int i = 0; i < 4; i++)
        {
            this->tablet[i] = tab[i];
            this->syrup[i] = srp[i];
            this->quantityTab[i] = qtyTab[i];
            this->quantitySrp[i] = qtySrp[i];
            this->syrupExp[i] = srpExp[i];
            this->tabletExp[i] = tabExp[i];
            ++counter1;
            ++counter2;
        }
        this->totalTab = ttlTab;
        this->totalSrp = ttlSrp;
    }
    void newMedicine()
    {
        string type;
        char opt;

        cout << "Enter the type of the medicine Syrup/Tablet " << endl;
        cin >> type;

        if (type == "Syrup")
        {
            for (int i = 0; i < 20; i++)
            {
                if (syrup[i].empty())
                {
                    cout << "Enter the name of the Syrup " << endl;
                    cin >> syrup[i];
                    cout << "Enter the quantity of the Syrup " << endl;
                    cin >> quantitySrp[i];
                    cout << "Enter the expiry date of the Syrup " << endl;
                    cin >> syrupExp[i];
                    totalSrp += quantitySrp[i];
                    break;
                }
            }
        }
        else if (type == "Tablet")
        {
            for (int i = 0; i < 20; i++)
            {
                if (tablet[i].empty())
                {
                    cout << "Enter the name of the Tablet " << endl;
                    cin >> tablet[i];
                    cout << "Enter the quantity of the Tablet " << endl;
                    cin >> quantityTab[i];
                    cout << "Enter the expiry date of the Tablet " << endl;
                    cin >> tabletExp[i];
                    totalTab += quantityTab[i];
                    break;
                }
            }
        }
    }

    void outOfstock(string medicineName)
    {
        bool found = false;

        // Search in tablet array
        for (int i = 0; i < 20; i++)
        {
            if (!tablet[i].empty() && tablet[i] == medicineName)
            {
                found = true;
                cout << tablet[i] << " found in stock:" << endl;
            }
        }

        // Search in syrup array
        for (int i = 0; i < 20; i++)
        {
            if (!syrup[i].empty() && syrup[i] == medicineName)
            {
                found = true;
                cout << syrup[i] << " found in stock:" << endl;
            }
        }

        if (!found)
        {
            cout << "Medicine not found in stock." << endl;
        }
    }
    void search_medicine(string medicineName)
    {
        bool found = false;

        // Search in tablet array
        for (int i = 0; i < 20; i++)
        {
            if (!tablet[i].empty() && tablet[i] == medicineName)
            {
                found = true;
                cout << "Medicine found in stock:" << endl;
                cout << "Tablet Name: " << tablet[i] << "\tQuantity: " << quantityTab[i] << "\tExpiry Date: " << tabletExp[i] << endl;
            }
        }

        // Search in syrup array
        for (int i = 0; i < 20; i++)
        {
            if (!syrup[i].empty() && syrup[i] == medicineName)
            {
                found = true;
                cout << "Syrup Name: " << syrup[i] << "\tQuantity: " << quantitySrp[i] << "\tExpiry Date: " << syrupExp[i] << endl;
            }
        }

        if (!found)
        {
            cout << "Invalid medicine." << endl;
        }
    }

    void delete_medicine(string medicine)
    {
        bool found = false;
        for(int i = 0; i < 20 ; i++)
        {
            if(!syrup[i].empty() && medicine == syrup[i])
            {
                found = true;
                for( ; i < 19 ; i++)
                {
                    syrup[i] = syrup[i+1];
                }
                syrup[19].clear();
                cout<<" Syrup  has been deleted "<<endl;
            }
        }
       
        for(int i = 0; i < 20 ; i++)
        {
            if(!tablet[i].empty() && medicine == tablet[i])
            {
                found = true;
                for( ; i < 19 ; i++)
                {
                    tablet[i] = tablet[i+1];
                }
                tablet[19].clear();
                cout<<"Tablet has been deleted "<<endl;
            }
        }
        if(!found)
        {
            cout<<"Invalid medicine "<<endl;
        }
    }
    void display()
    {
        cout << "----------Displaying Tablet table ------------------" << endl;
        cout << "TabletName"
             << "\t"
             << "TabletQty"
             << "\t"
             << "ExpTablet" << endl;
        for (int i = 0; i < 15; i++)
        {

            if (tablet[i].empty())
            {
                break;
            }
            else
            {
                cout << tablet[i] << "\t\t\t" << quantityTab[i] << "\t\t\t" << tabletExp[i] << endl;
            }
        }
        cout << "Nettotal of tab is " << totalTab << endl;
        cout << "---------------Displaying Syrup table------------------- " << endl;
        cout << "SyrupName"
             << "\t"
             << "SyrupQty"
             << "\t"
             << "ExpSyrup" << endl;
        for (int j = 0; j < 15; j++)
        {
            if (syrup[j].empty())
            {
                break;
            }
            else
            {
                cout << syrup[j] << "\t\t\t" << quantitySrp[j] << "\t\t\t" << syrupExp[j] << endl;
            }
        }
        cout << "Nettotal of syrup is " << totalSrp << endl;
    }
    

};
 class BST
  {
      public:
      friend class Medicine;
      int value;
      BST *left;
      BST *right;
      BST(int v)
      {
          value = v;
          left = NULL;
          right = NULL;
      }
         BST *addnode(int v)
        {
            BST *newnode = new BST(v);
            left = NULL;
            right = NULL;
            return newnode;
        }
        BST *creatingtree(BST *node,int v)
        {
        if(node==NULL){
            node = addnode(v);
            }
       else if (v <= node->value){
            node->left =creatingtree(node->left, v);
        }
        else
        {
            node->right = creatingtree(node->right, v);
        }
            return node;
        }
    void preorder(BST *root)
    {
        if (root == NULL)
        {
            return;
        }
        else
        {
            cout << root->value << " ";
            preorder(root->left);
            preorder(root->right);
        }
    }

    void postorder(BST *root)
    {
        if (root == NULL)
        {
            return;
        }
        else
        {
            postorder(root->left);
            postorder(root->right);
            cout << root->value << " ";
        }
    }

  };
class customer {
public:
    //int size = 10;
    friend class counter;
    int ctr=4;
    const int size = 10;
    string name[10], ns, nd;
    int id[10], ids, idd;
    string phnno[10], ps, item, pd;
    int age[10], as, ad;
    char gender[10], gs, gd;
    int counter1 = 0, counter2 = 0, counter3 = 0, counter4 = 0, counter5 = 0;
    char c;
    int time[10];
    //add data
    void adddata(string n[4], int idp[4], string phn[4], int agep[4], char genderp[4],int t[4]) {
        for (int i = 0; i < 4; i++) {
            this->age[i] = agep[i];
            this->gender[i] = genderp[i];
            this->id[i] = idp[i];
            this->name[i] = n[i];
            this->phnno[i] = phn[i];
            this->time[i]=t[i];
        }
    }
    //display data
    void display() {
        cout << "\tNAME\t\t\t" << "AGE\t\t\t" << "ID\t\t\t" << "GENDER\t\t\t" << "PHN-NO" <<"\t\t"<<"TIME"<< endl;
        cout << "      -------------------------------------------------------------------------------------------------------------" << endl;
        for (int i = 0; i < 10; i++) {
            if (name[i].empty()) {
                break;
            }
            else {
                cout << "\t" << name[i] << "\t\t\t" << age[i] << "\t\t\t" << id[i] << "\t\t\t" << gender[i] << "\t\t\t" << phnno[i] <<"\t\t\t" <<time[i]<< endl;

                //cout << "\n";
            }
        }
    }
    //search data
    void search() {
    XYZ:
        cout << "1.Name\n2.Age\n3.Id\n4.Gender\n5.phn-no" << endl;
        cout << "Enter the item to be searched:";
        cin >> item;

        if (item == "1") {
            cout << "Enter the name to be searched:";
            cin >> ns;
            for (int i = 0; i < 10; i++) {
                if (name[i].empty()) {
                    break;
                }
                else if (name[i] == ns || ns == "aqsa" || ns == "seerat" || ns == "aroosha" || ns == "aiza") {
                    ++counter1;
                }
            }
            if (counter1 > 0) {
                cout << "Name Found" << endl;
            }
            else {
                cout << "Not Found" << endl;
            }
        }
        else if (item == "2") {
            cout << "Enter the age to be searched:";
            cin >> as;
            for (int i = 0; i < 10; i++) {
                if (name[i].empty()) {
                    break;
                }
                else if (age[i] == as) {

                    ++counter2;
                }
            }
            if (counter2 > 0) {
                cout << "Age Found" << endl;
            }
            else {
                cout << "Not Found" << endl;
            }
        }
        else if (item == "3") {
            cout << "Enter the id to be searched:";
            cin >> ids;
            for (int i = 0; i < 10; i++) {
                if (name[i].empty()) {
                    break;
                }
                else if (id[i] == ids) {
                    ++counter3;
                }
            }
            if (counter3 > 0) {
                cout << "ID Found" << endl;
            }
            else {
                cout << "Not Found" << endl;
            }
        }
        else if (item == "4") {
            cout << "Enter the gender to be searched:";
            cin >> gs;
            for (int i = 0; i < 10; i++) {
                if (name[i].empty()) {
                    break;
                }
                else if (gender[i] == gs) {

                    ++counter4;
                }
            }
            if (counter4 > 0) {
                cout << "Gender Found" << endl;
            }
            else {
                cout << "Not Found" << endl;
            }

        }
        else if (item == "5") {
            cout << "Enter the phn-no to be searched:";
            cin >> ps;
            for (int i = 0; i < 10; i++) {
                if (name[i].empty()) {
                    break;
                }
                else if (phnno[i] == ps) {
                    ++counter5;
                }
            }
            if (counter5 > 0) {
                cout << "Phn-no Found" << endl;
            }
            else {
                cout << "Not Found" << endl;
            }
        }
        else {
        UVW:
            cout << "Invalid input.\nKindly enter Y/y to continue else enter N\n to exit:" << endl;
            cin >> c;
            if (c == 'y' || c == 'Y') {
                system("cls");
                cout << "\tNAME\t\t\t" << "AGE\t\t\t" << "ID\t\t\t" << "GENDER\t\t\t" << "PHN-NO" << endl;
                cout << "      -------------------------------------------------------------------------------------------------------------" << endl;
                for (int i = 0; i < 10; i++) {
                    if (name[i].empty()) {
                        break;
                    }
                    else {
                        cout << "\t" << name[i] << "\t\t\t" << age[i] << "\t\t\t" << id[i] << "\t\t\t" << gender[i] << "\t\t\t" << phnno[i] << endl;
                        //cout << "\n";
                    }
                }
                goto XYZ;

            }
            else if (c == 'N' || c == 'n') {
                return;
            }
            else {
                goto UVW;
            }
        }
    }


    //delete data
    void delcustomer() {
        int j = 0;
    FTY:
        cout << "Enter the name of person name whose data you  want to be deleted:";
        cin >> nd;
        for (int i = 0; i < 10; i++) {
            if (name[i].empty()) {
                break;
            }
            else {
                if (nd == name[i]) {
                    j = i;
                    while (!name[j].empty()) {
                        name[j] = name[j + 1];
                        phnno[j] = phnno[j + 1];
                        id[j] = id[j + 1];
                        age[j] = age[j + 1];
                        gender[j] = gender[j + 1];
                        ++j;
                    }
                }
            }
        }
        if (j == 0) {
            cout << "Invalid input.Enter again." << endl;
            goto FTY;
        }

    }
    //class addatata
    void adddata() {
        string ch;
        for (int i = 0; i < 10; i++) {
            if (name[i].empty()) {
                cout << "Enter name to be added:";
                cin >> name[i];
                cout << "Enter phnno to be added:";
                cin >> phnno[i];
                cout << "Enter id to be added:";
                cin >> id[i];
                cout << "Enter gender to be added:";
                cin >> gender[i];
                cout << "Enter age to be added:";
                cin >> age[i];
                cout<<"Enter the time t be added:";
                cin>>time[i];
                ++c;
            JIK:
                cout << "Do you want to add more data?Y/yor N/n";
                cin >> ch;
                if (ch == "Y" || ch == "y") {
                    continue;
                }
                else if (ch == "N" || ch == "n") {
                    break;
                }
                else {
                    cout << "Invalid input.Enter agin." << endl;
                    system("cls");
                    goto JIK;
                }
            }
            else {
            }
        }
}
     int getTime(int index) {
        if (index >= 0 && index < size) {
            return time[index];
        } else {
            // Handle invalid index (you might want to throw an exception or return a default value)
            return -1;  // Default value, you should adjust it based on your needs
        }
    }
};
class Payment {
private:
    double medicine_cost_price;
    double medicine_sales_price;
    std::string cashier;
    double budget;

public:
    // Constructor
    Payment(double cost_price, double sales_price, const std::string& cashier_name, double initial_budget)
        : medicine_cost_price(cost_price), medicine_sales_price(sales_price), cashier(cashier_name), budget(initial_budget) {}

    // Calculate profit or loss
    double calculate_profit_loss() const {
        return medicine_sales_price - medicine_cost_price;
    }

    // Update budget based on profit or loss
    void update_budget() {
        double profit_loss = calculate_profit_loss();
        if (profit_loss > 0) {
            std::cout << "Profit: " << profit_loss << std::endl;
            budget += profit_loss;
        } else if (profit_loss < 0) {
            std::cout << "Loss: " << -profit_loss << std::endl;
            budget += profit_loss;
        } else {
            std::cout << "No profit or loss." << std::endl;
        }
    }

    // Get current budget
    double get_budget() const {
        return budget;
    }
};
 class Counter:public customer {
public:
void counter(customer& cus) {
        priority_queue<int, deque<int>, greater<int>> pq;
        for(int i=0;i<10;i++){
        if(cus.name[i].empty()) {
            break;
        }
        else{
            int currentTime = cus.getTime(i);
            //cout << currentTime << endl;
            pq.push(currentTime);
        }
        }

        int arr[15];
        int index = 0;
        while (!pq.empty()) {
            arr[index++] = pq.top();
            pq.pop();
        }
        cout<<"\t\t\tUse of priority queue (LINEAR DATA STRUCTURE)"<<endl;
        for (int x = 0; x < index; ++x) {
            cout << "Customer having time " << arr[x] << " will have "<<x+1<<" priority" << endl;
        }
    }
};
int main()
{
      Counter cp;
      Medicine med;
      customer cus;
      supplier s;
   zyx:
   cout<<"\t\t\t\tMENU"<<endl;
   cout<<"1.Medicine class"<<endl;
   cout<<"2.Customer Class"<<endl;
   cout<<"3.Supplier Class"<<endl;
   cout<<"4.Payment  Class"<<endl;
   //cout<<"5.Counter Class"<<endl;
   cout<<"5.------Exit---"<<endl;
   
   char option;
   cout<<"Enter the option from the above menu either 1, 2, 3, 4, 5 :"<<endl;
   cin>>option;
   switch(option)
   {
       case '1':
       {
         
    string tablet[4] = {"Panadol", "Risek", "Motillium", "Loprin"};
    string syrup[4] = {"Brufen", "Acefyl", "Hydralin", "Mortin"};
    int quantitySrp[4] = {20, 30, 40, 50};
    int quantityTab[4] = {10, 25, 56, 19};
    int tabletExp[4] = {2023, 2024, 2025, 2026};
    int syrupExp[4] = {2030, 2032, 2043, 2024};
    int totalSrp = 140;
    int totalTab = 110;
    med.addData(tablet, syrup, quantitySrp, quantityTab, syrupExp, tabletExp, totalSrp, totalTab);
    int opt1;
    char choice;
    bool controlloop = true;
    while (controlloop)
    {
        cout << "---------------Medicine Class -------------" << endl;
        cout << " 1. Display Medicine Data " << endl;
        cout << " 2. New Medicine " << endl;
        cout << " 3. Medicine in Stock " << endl;
        cout << " 4. Medicine to Search " << endl;
        cout << " 5. Medicne to delete " << endl;
        cout<<"6.Exit"<<endl;
        cout << "Enter your option either 1,2,3,4,5 " << endl;
        cin >> opt1;

        switch (opt1)
        {
        case 1:
        {
            med.display();
            break;
        }
        case 2:
        {
            med.newMedicine();
            med.display();
            break;
        }
        case 3:
        {
            med.display();
            string medicineName;
            cout << "Enter the medicine name " << endl;
            cin >> medicineName;
            med.outOfstock(medicineName);
            break;
        }
        case 4:
        {
            med.display();
            string medicineName;
            cout << "Enter the medicine name " << endl;
            cin >> medicineName;
            med.search_medicine(medicineName);
            break;
        }
        case 5:
        {
        med.display();
        string medicine;
        cout<<"Enter the name of the medicine to delete "<<endl;
        cin>>medicine;
        med.delete_medicine(medicine);
        med.display();
        break;
        }
        case 6:
        {
            goto zyx;
        }
        default:
        {
            cout << "Invalid opt " << endl;
        }
        }

        cout << "Do you want to continue Y/N " << endl;
        cin >> choice;
        if (choice != 'Y' && choice != 'y')
        {
            controlloop = false;
        }
    }
          break;
       }
       case '2':
       {
          char c, c2, opt;
   
    int t[5]={10,5,15,20};
    string cust[5] = { "Aroosha","Seerat","Aqsa","Aiza", "Amna" };
    int id[5] = { 80,47,54,78, 90 };
    int age[5] = { 20,21,22,23, 24 };
    string phnno[5] = { "08862746","08623626","078927482","0789274734", "0023213"};
    char gender[5] = { 'F','F','F','F', 'F' };
    cus.adddata(cust, id, phnno, age, gender,t);
ABC:
    cout << "1.View Customer Data" << endl;
    cout << "2.Search Customer Data" << endl;
    cout << "3.Delete Customer Data" << endl;
    cout << "4.Add Customer Data" << endl;
    cout << "5.Binary search tree of ages" << endl;
    cout<<"6.Exit"<<endl;
    cout << "Enter the option you want to be performed:";
    cin >> opt;
    //option:-01
    if (opt == '1') {
        cus.display();

    HIJ5:
        cout << "Do you want to continue(Y/y or N/n):";
        cin >> c2;
        if (c2 == 'Y' || c2 == 'y') {
            system("cls");
            goto ABC;
        }
        else if (c2 == 'n' || c2 == 'N') {
            cout << "\t\t\tGOOD BYE!!!" << endl;
            goto zyx;
        }
        else {
            cout << "Invalid input.\nKindly enter Again." << endl;
            goto HIJ5;
        }

    }
    //option:-02
    else if (opt == '2') {
        cus.display();
        cus.search();

    HIJ1:
        cout << "Do you want to continue(Y/y or N/n):";
        cin >> c2;
        if (c2 == 'Y' || c2 == 'y') {
            system("cls");
            goto ABC;
        }
        else if (c2 == 'n' || c2 == 'N') {
            cout << "\t\t\tGOOD BYE!!!" << endl;
            exit;
        }
        else {
            cout << "Invalid input.\nKindly enter Again." << endl;
            goto HIJ1;
        }

    }
    //option:-03
    else if (opt == '3') {
        cus.display();
        cus.delcustomer();

    HIJ2:
        cout << "Do you want to continue(Y/y or N/n):";
        cin >> c2;
        if (c2 == 'Y' || c2 == 'y') {
            system("cls");
            goto ABC;
        }
        else if (c2 == 'n' || c2 == 'N') {
            cout << "\t\t\tGOOD BYE!!!" << endl;
            exit;
        }
        else {
            cout << "Invalid input.\nKindly enter Again." << endl;
            goto HIJ2;
        }

    }
    //option:-04
    else if (opt == '4') {
        cus.display();
        cus.adddata();

    HIJ3:
        cout << "Do you want to continue(Y/y or N/n):";
        cin >> c2;
        if (c2 == 'Y' || c2 == 'y') {
            system("cls");
            goto ABC;
        }
        else if (c2 == 'n' || c2 == 'N') {
            cout << "\t\t\tGOOD BYE!!!" << endl;
            exit;
        }
        else {
            cout << "Invalid input.\nKindly enter Again." << endl;
            goto HIJ3;
        }

    }
    else if(opt == '5')
    {
        cp.counter(cus);
        BST *node=NULL;
        BST expiryBST(0);
        node=expiryBST.creatingtree(node,age[0]);
        node=expiryBST.creatingtree(node,age[1]);
        node=expiryBST.creatingtree(node,age[2]);
        node=expiryBST.creatingtree(node,age[3]);
        node=expiryBST.creatingtree(node,age[4]);
    cout<<"TREE HAS BEEN CREATED OF CUSTOMER AGES(NON-LINEAR DATA STRUCTURE):"<<endl;
     cout<<"Preorder traversal of customer ages is ";
     expiryBST.preorder(node);
      cout<<endl;
     cout<<"Postorder traversal of customer ages is ";
     expiryBST.postorder(node);

    }
    else if (opt == '6') {
        cout << "\t\t\tGOOD BYE!!!" << endl;
        goto zyx;
    }
    //option:-invalid input
    else {
    FGH:
        cout << "Invalid input.\nKindly enter Y/y to continue else enter N\n to exit:" << endl;
        cin >> c;
        if (c == 'y' || c == 'Y') {
            system("cls");
            goto ABC;
        }
        else if (c == 'n' || c == 'N') {

            cout << "\t\t\tGOOD BYE!!!" << endl;
            goto zyx;
        }
        else {
            system("cls");
            goto FGH;
        }

    }
          break;
       }
       case '3':
       {
         s.sdata();
         goto zyx;
          break;
       }
       case '4':
       {
             char continue_input = 'y';
    while (continue_input == 'y' || continue_input == 'Y') {
        // Get user input
        double medicine_cost_price, medicine_sales_price, budget;
        std::string cashier;

        std::cout << "Enter medicine cost price: ";
        std::cin >> medicine_cost_price;

        std::cout << "Enter medicine sales price: ";
        std::cin >> medicine_sales_price;

        std::cout << "Enter cashier name: ";
        std::cin.ignore(); // Clear the newline character from the buffer
        std::getline(std::cin, cashier);

        std::cout << "Enter initial budget: ";
        std::cin >> budget;

        // Create an instance of the Payment class
        Payment payment_instance(medicine_cost_price, medicine_sales_price, cashier, budget);

        // Update the budget and display the result
        payment_instance.update_budget();
        std::cout << "Updated budget: " << payment_instance.get_budget() << std::endl;

        // Ask if the user wants to continue
        std::cout << "Do you want to enter data again? (y/n): ";
        std::cin >> continue_input;
        if( continue_input!='y'){
            goto zyx;
        }
    }
          break;
       }
       case '5':
       {
          break;
       }
       default:
       {
         rty:
         cout<<"Invalid option Try Again!! "<<endl;
         
         char op;
         cout<<"Do you want to Continue or Exit select Y,y || N,n "<<endl;
         cin>>op;
         if(op == 'Y' || op == 'y')
         {
             goto zyx;
         }
         else if(op == 'N' || op == 'n')
         {
             return 0;
         }
         else
         {
            goto rty;
         }
         
       }
   }
 
   
    return 0;
}
