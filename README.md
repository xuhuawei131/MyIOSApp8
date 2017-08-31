# MyIOSApp8
16-1 && 16-2<br/>
UIPickerView 的用法<br/>

#pragma mark --datasource<br/>
// 返回 几列数据<br/>
- (NSInteger)numberOfComponentsInPickerView:(UIPickerView *)pickerView{<br/>
    return 2;<br/>
}<br/>
//第component列 有几行数据<br/>
- (NSInteger)pickerView:(UIPickerView *)pickerView numberOfRowsInComponent:(NSInteger)component{<br/
    
    if(component==0){><br/>
        return self.cityArray.count;><br/>
    }else if(component==1){><br/>
        return [self getAreaArray].count;><br/>
    }><br/>
    return 0;><br/>
}><br/>


#pragma mark--- delegate><br/>
//第component 第row行 返回的字符串作为title><br/>
- (nullable NSString *)pickerView:(UIPickerView *)pickerView titleForRow:(NSInteger)row forComponent:(NSInteger)component {
    ><br/>
    if(component==0){//第一列><br/>
        return self.cityArray[row];><br/>
    }else if(component==1){//第二列><br/>
        int firstIndex= [self currentFirstIndex];><br/>
        NSArray* childArray=[self getAreaArray:firstIndex];><br/>
        return childArray[row];><br/>
    }><br/>
     return @"xxx";><br/>
}><br/>

//滑动选中的回调><br/>
- (void)pickerView:(UIPickerView *)pickerView didSelectRow:(NSInteger)row inComponent:(NSInteger)component{><br/>
    if(component==0){><br/>
        [pickerView reloadComponent:1];><br/>
        [pickerView selectRow:0 inComponent:1 animated:TRUE];><br/>
    }><br/>
}><br/>

- (void)viewDidLoad {><br/>
    [super viewDidLoad];><br/>
    self.pickerView.dataSource=self;><br/>
    self.pickerView.delegate=self;><br/>
    
    self.cityArray=@[@"北京",@"天津",@"上海",@"重庆"];><br/>
    
    NSArray* beijing=@[@"海淀",@"东城",@"西城",@"朝阳"];><br/>
    
    NSArray* tianjin=@[@"南开1",@"南开2",@"南开3",@"南开4"];><br/>
    NSArray* shanghai=@[@"徐汇1",@"徐汇2",@"徐汇3",@"徐汇4"];><br/>
    NSArray* chongqing=@[@"山顶1",@"山顶2",@"山顶3",@"山顶4"];><br/>
    self.allArray=@[beijing,tianjin,shanghai,chongqing];><br/>
}><br/>

