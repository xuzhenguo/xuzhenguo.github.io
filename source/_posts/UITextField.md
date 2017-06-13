---
layout: uitextview
title: UITextField
date: 2017-06-13 11:04:59
tags:
---

## UITextView 变 UITextField ##

//
//  WCPurchaseOrdeDetailsTextImageCell.m
//  wecabin
//
//  Created by 许震国 on 17/6/13.
//  Copyright © 2017年 共享天地（武汉）科技有限公司. All rights reserved.
//

```OC
#import "WCPurchaseOrdeDetailsTextImageCell.h"
@interface WCPurchaseOrdeDetailsTextImageCell ()<UITextViewDelegate>
@property(nonatomic,copy)NSString *placeholderStr;
@property(nonatomic,retain)UITextView *myTextView;
@end
@implementation WCPurchaseOrdeDetailsTextImageCell

> - (instancetype)initWithStyle:(UITableViewCellStyle)style reuseIdentifier:(nullable NSString *)reuseIdentifier{
self = [super initWithStyle:style reuseIdentifier:reuseIdentifier];
if (!self) return nil;
[self addSubView];
return self;
}
-(void)addSubView{

UIView *superView = self.contentView;
self.placeholderStr = @"对商品有哪些满意或者不满意的呢？写出来吧~";
[superView addSubview:self.myTextView];

}


-(UITextView *)myTextView{
if (_myTextView == nil) {

_myTextView = [[UITextView alloc]initWithFrame:CGRectMake(0,8, SCREEN_WIDHT, SCALE_WIDHT_TO(100))];
_myTextView.textColor = COLORTHREE;
_myTextView.font = [UIFont fontWithName:@"Helvetica-Bold" size:14];
_myTextView.delegate = self;
_myTextView.backgroundColor = COLORTHIRTEENTH;
_myTextView.text = self.placeholderStr;
}
return _myTextView;
}
//编辑结束调用
-(void)textViewDidEndEditing:(UITextView *)textView{
NSLog(@"%@",textView.text);
if ([textView.text isEqualToString:@""]) {
textView.text = _placeholderStr;
textView.textColor = COLORTHREE;
}

}
//触发编辑调用
- (void)textViewDidBeginEditing:(UITextView *)textView{
if ([textView.text isEqualToString:_placeholderStr]) {
textView.text = @"";
textView.textColor = COLORFIVE;
}
}
//编辑中调用
- (void)textViewDidChange:(UITextView *)textView{
if (textView.text.length >200)
{
[self showHint:@"不允许输入超过201字"];
textView.text = [textView.text substringToIndex:200];

}
}
@end


```

作者 [@许震国][3]     
2016 年 07月 07日    

[1]: https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown
[2]: https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown#cmd-markdown-高阶语法手册
[3]: http://weibo.com/ghosert
[4]: http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference

