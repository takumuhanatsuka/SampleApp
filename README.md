SampleApp
=========

My FirstApp

#import "ViewController.h"

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad
{
    [super viewDidLoad];
    // Do any additional setup after loading the view, typically from a nib.
    //_imageArrayの初期化
    _imageArray = @[@"j1.jpeg", @"j2.jpeg", @"j3.jpeg", @"j4.jpeg",@"5.jpeg",@"6.jpeg",@"7.jpeg"];
    [portScrollView setContentSize:CGSizeMake(640,460)];

}

- (void)didReceiveMemoryWarning
{
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

- (void) touchesBegan:(NSSet *) touches withEvent: (UIEvent *) event
{
    UITouch * touchedObj = [[event allTouches] anyObject];
    if (touchedObj.view.tag ==_imageView.tag) {
        NSLog(@"imageViewがタップされた！");
        if(_imageArray.count == _imageArraySelectedIndex + 1) {
            //_imageArray.count == _imageArraySelectedIndex + 1→配列の終端が表示されている時
            _imageArraySelectedIndex = 0;
        }
        else {
            //配列の終端以外が表示されている時は_imageArraySelectedIndexをインクリメント
            _imageArraySelectedIndex++;
        }
        NSLog(@"_imageArraySelectedIndex = %d, currentImage=%@", _imageArraySelectedIndex, _imageArray[_imageArraySelectedIndex]);
        //_imageArraySelectedIndexに対応するイメージを_imageView.imageにセット
        _imageView.image =  [UIImage imageNamed:_imageArray[_imageArraySelectedIndex]];
        
    }
}

@end
