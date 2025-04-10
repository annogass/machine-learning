# machine-learning

პროექტის აღწერა
ეს პროექტი მოიცავს Kaggle-ის "House Prices: Advanced Regression Techniques" კონკურსისთვის შემუშავებულ მოდელს, რომელიც პროგნოზირებს სახლების ფასებს 79 განმარტებითი ცვლადის გამოყენებით.

რეპოზიტორიის სტრუქტურა:
model_experiment.ipynb - ძირითადი სამუშაო ნოუთბუქი რომელშიც დავწერე დავალება. შევქმენი რამდენიმე მოდელი და დავლოგე რამდენიმე ექსპერიმენტი თითოეულ მოდელზე.
model_inference.ipynb -  test set ზე პროგნოზი, საუკეთესო მოდელის გამოყენებით  დავაგენერირე submissions, რომელიც ავტვირთე kaggle - ზე და შევაფასე  ჩემი  მოდელი. 
readme-ჩემი ნამუშევრის დეტალური აღწერა.

Feature Engineering:
ნალების გასუფთავება
გამოტოვებული მნიშვნელობები:
მე გამოვიყენე რიცხვითი და კატეგორიული ცვლადები
რიცხვითი ცვლადებისთვის NaN მნიშვნელობები შეივსო 0-ით
კატეგორიული ცვლადებისთვის NaN მნიშვნელობები შეივსო "NO"-თი

გამოტოვებული სვეტები:
წავშალე ის სვეტები, სადაც გამოტოვებული მნიშვნელობების პროცენტი 80%-ზე მეტი იყო რადგან როგორც ვიცით one hot დაამატებდა იმდენ ახალ სვეტს 
რამდენი უნიკალური მნიშვნელობაც არის სვეტში. ექსპერიმენტისთვის ვცადე woe -ს გამოსაყენებლად ორი სახის th=20 ერთი დიდი რაც woe-თი ცოტა სვეტს დაამუსავებდა და ძირითადად one hot-ით იმუსავებდა შემდეგ კი th=3 რამაც ბაზიზ უმეტესი ნაწილი woe-თი დაამუსავა, მეორე მიდგომამ საგრძნობლად უკეთესი შედეჰგი გამოიღო.

კატეგორიული ცვლადების დამუშავება

შევქმენით ორი კატეგორია:
WOE (Weight of Evidence) კოდირება კატეგორიული ცვლადებისთვის, რომლებსაც >3 უნიკალური მნიშვნელობა ჰქონდა
One-Hot კოდირება დარჩენილი კატეგორიული ცვლადებისთვის

WOE ტრანსფორმაცია:
გამოვთვალეთ თითოეული კატეგორიის WOE მნიშვნელობა სამიზნე ცვლადთან (SalePrice) მიმართებაში
შევქმენით WOE რუკა თითოეული კატეგორიული ცვლადისთვის

Feature Selection:
მაღალი კორელაციის მქონე ცვლადები:
იდენტიფიცირებული იქნა მაღალი კორელაციის მქონე (>0.8) ცვლადების წყვილები
წავშალე ის ცვლადები, რომლებსაც ნაკლები კორელაცია ჰქონდა სამიზნე ცვლადთან
RFE (Recursive Feature Elimination):
გამოვიყენე LinearRegression მოდელი RFE-სთან ერთად
შევარჩიეთ საუკეთესო 15 ცვლადი
ვიზუალიზაცია გავაკეთე ცვლადების რანჟირების შესახებ

Training:

მოდელები:
Linear Regression:
საბაზისო მოდელი
გამოიყენება RFE ცვლადების შერჩევაში
MLflow-ით ტრეკინგი:
ჩავწერე ექსპერიმენტები MLflow-ში
ტრეკინგი მოიცავდა მეტრიკებს (RMSE, BIAS, VARIANCE) 

Random Forest:
გამოიყენება RFE ცვლადების შერჩევაში
MLflow-ით ტრეკინგი:
ჩავწერე ექსპერიმენტები MLflow-ში
ტრეკინგი მოიცავდა მეტრიკებს (RMSE, BIAS, VARIANCE) 

XGBRegressor:
გამოიყენება RFE ცვლადების შერჩევაში
MLflow-ით ტრეკინგი:
ჩავწერე ექსპერიმენტები MLflow-ში
ტრეკინგი მოიცავდა მეტრიკებს (RMSE, BIAS, VARIANCE) 


ტავდაპირველად ვცადე RFE-ს გარეშე მაგრამ როცა RFE გამოვიყენე და გადავარცჰიე 60 სვეტი უკეთესი შედეგი მივიღე ამიტომ საბოლოო შედეგი არის მისი გამოყენებით.

საუკეთესო მოდელი:
https://dagshub.com/agasi22/machine-learning.mlflow/#/experiments/3/runs/8a078eb0ebe24b1fbacd6ee767a42b98
საბოლოო მოდელის შერჩევა განხორციელდა შემდეგი კრიტერიუმების მიხედვით:

ყველაზე დაბალი RMSE
მოდელის ინტერპრეტაციულობა
რეპოზიტორიის სტრუქტურა




MLflow Tracking:
model_xgb experiments - https://dagshub.com/agasi22/machine-learning.mlflow/#/experiments/3?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D

model_rf experiments - https://dagshub.com/agasi22/machine-learning.mlflow/#/experiments/2?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D

model_lr experiments- https://dagshub.com/agasi22/machine-learning.mlflow/#/experiments/1?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D

final(best) model- https://dagshub.com/agasi22/machine-learning.mlflow/#/experiments/3/runs/8a078eb0ebe24b1fbacd6ee767a42b98

MLflow-ის გამოყენებით ჩავწერე ყველა ექსპერიმენტი, მათ შორის:

მოდელის პარამეტრები
მეტრიკები (RMSE, BIAS, VARIANCE)
ფიჩერების მნიშვნელობა

ჩემი საუკეტესო მოდელი არის ბოლო model_xgb.
დასკვნა

ამ პროექტში ჩვენ განვახორციელეთ:

მონაცემთა საფუძვლიანი დამუშავება და გასუფთავება
კატეგორიული ცვლადების ეფექტური გადაყვანა რიცხვით ფორმატში
ფიჩერების შერჩევა როგორც კორელაციის, ასევე RFE მეთოდების გამოყენებით
მრავალი მოდელის ტესტირება და საუკეთესოს შერჩევა
საბოლოო მოდელმა აჩვენა X% სიზუსტე ტესტის მონაცემებზე, რაც ამ კატეგორიის პრობლემებისთვის კონკურენტუნარიან შედეგს წარმოადგენს.
