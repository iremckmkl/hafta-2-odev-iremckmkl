# Gereken sorguyu çalıştırdıktan sonra sample.content_category ve sample.content_category_target tablolarının içerikleri birebir aynı olmalıdır!

``` SQL
merge irem_cakmakli.content_category t
using irem_cakmakli.content_category_20201222_00_59 s
on t.id=s.id
when not matched by source then update set a.is_deleted=true
when not matched by target then insert(cdc_date,is_deleted,id,category) values(s.cdc_date,s.is_deleted,s.id,s.category)
When Matched and t.cdc_date <> s.cdc_date Or t.category<>s.category Then
Update Set t.cdc_date=s.cdc_date,t.category=s.category;

```
``` SQL
select *
from irem_cakmakli.content_category test
full join irem_cakmakli.content_category_target targt
on farm_fingerprint(to_json_string(test.id)) =farm_fingerprint(to_json_string(targt.id))
where targt.id is null or targt.id is null
```
