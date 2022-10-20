Select (a.id) as Id from weather a, weather b
where
datediff(a.recordDate , b.recordDate)=1 and a.temperature > b.temperature ;