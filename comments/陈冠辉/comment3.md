
# Hotel01项目评价

## 项目优点

1. **项目结构清晰**
   - 采用了模块化的设计思想，将不同功能模块分开存放
   - 目录结构合理，包括：
     - `Data/`: 数据处理相关
     - `Rooms/`: 房间管理
     - `Users/`: 用户管理
     - `Menu/`: 菜单界面
     - `Datafile/`: 数据文件存储

2. **面向对象设计**
   - 使用了面向对象的设计方法，如用户（User）和用户角色（UserRole）的分离
   - 体现了良好的封装性原则

3. **功能模块划分**
   - 将酒店管理系统的核心功能进行了清晰的划分
   - 便于后期维护和扩展
4. **优雅**
   - 代码确实挺优雅的
   - Menu部分写的非常好
   - UserRole枚举类和Steam流操作


## 项目不足

1. **项目文档不完善**

   - README.md文件内容较少，缺乏详细的项目说明和使用指南
   - 代码注释可能不够充分

2. **项目不够完善**

   - 作为普通用户:

     - 无法查看自己预定的房间

   - 作为管理员用户：

     - 缺少相应的房间管理操作

   - other:

     - 资金添加操作放在判断之后，导致充值后没有变为会员

       ```java
           private static void addMoney(User user, DataSave data) {
               Scanner scanner = new Scanner(System.in);
               System.out.print("请输入充值金额：");
               double amount = scanner.nextDouble();
               scanner.nextLine();
               System.out.println("充值成功！");
               if(user.getSalary()>=1000){
                   user.setRole(UserRole.UP);
                   System.out.println("你已成功变成会员，可享受9折折扣");
                   user.setDiscount(9);
               }
               user.setSalary(user.getSalary() + amount);
               data.saveUsers(new ArrayList<>(List.of(user)));
           }
       ```

     - 缺少鉴权操作，可以退订任何人的房间

       ```java
       public static void checkout(User user, ArrayList<Room> rooms, DataSave data) {
           Scanner scanner = new Scanner(System.in);
           System.out.print("输入要退房的房间号：");
           int roomNumber = scanner.nextInt();
           boolean flag = false;
           for (Room room : rooms) {
               if(room.getRoomID() == roomNumber&&(!room.isBook())){
                   flag = true;
                   room.setBook(true);
                   System.out.println("退房成功");
                   data.saveRooms(rooms);
                   break;
               }
           }
           if(!flag){
               System.out.println("没有订这个房间");
           }
       
       }
       ```

     - 资金类型使用double可能会造成潜在的风险

     



3. **建议改进点**
   - 建议添加单元测试
   - 可以更加真实的模拟酒店预定流程
   - 可以考虑引入日志系统
   - 可以考虑使用设计模式优化代码结构

## 总体评价

该项目是一个基础的酒店管理系统，整体架构设计合理，代码优雅，能够完成考核所要求的基本内容，但还有提升空间。

## 学习建议

1. 学习Java设计模式
2. 补充git相关知识
3. 学习单元测试编写
4. 掌握文档编写规范
5. 了解日志框架的使用


# keyValue项目评价

已经有初步的样子了，能完成到这里也很不错，希望你能坚持下去！

