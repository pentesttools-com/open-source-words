uitableview fdtemplatelayoutcell overview template auto layout cell for automatically uitableviewcell height calculating basic usage if you have a self satisfied cell then all you have to do is objc import uitableview fdtemplatelayoutcell h cgfloat tableview uitableview tableview heightforrowatindexpath nsindexpath indexpath return tableview fd heightforcellwithidentifier reuse identifer configuration id cell configure this cell with data same as what youve done in tableview cellforrowatindexpath like cell entity self feedentities indexpath row height caching api since ios8 tableview heightforrowatindexpath will be called more times than we expect we can feel these extra calculations when scrolling so we provide another api with cache by index path objc cgfloat tableview uitableview tableview heightforrowatindexpath nsindexpath indexpath return tableview fd heightforcellwithidentifier identifer cachebyindexpath indexpath configuration id cell configurations or if your entity has an unique identifier use cache by key api objc cgfloat tableview uitableview tableview heightforrowatindexpath nsindexpath indexpath entity entity self entities indexpath row return tableview fd heightforcellwithidentifier identifer cachebykey entity uid configuration id cell configurations frame layout mode fdtemplatelayoutcell offers 2 modes for asking cells height auto layout mode using systemlayoutsizefittingsize frame layout mode using sizethatfits generally no need to care about modes it will automatically choose a proper mode by whether you have set auto layout constrants on cells content view if you want to enforce frame layout mode enable this property in your cells configuration block objc cell fd enforceframelayout yes and if youre using frame layout mode you must override sizethatfits in your customized cell and return content views height separator excluded cgsize sizethatfits cgsize size return cgsizemake size width a b c d e debug log debug log helps to debug or inspect what is this fdtemplatelayoutcell extention doing turning on to print logs when calculating precaching or hitting cache default to no log by nslog objc self tableview fd debuglogenabled yes it will print like this objc fdtemplatelayoutcell layout cell created fdfeedcell fdtemplatelayoutcell calculate 0 0 233 5 fdtemplatelayoutcell calculate 0 1 155 5 fdtemplatelayoutcell calculate 0 2 258 fdtemplatelayoutcell calculate 0 3 284 fdtemplatelayoutcell precached 0 3 284 fdtemplatelayoutcell calculate 0 4 278 5 fdtemplatelayoutcell precached 0 4 278 5 fdtemplatelayoutcell hit cache 0 3 284 fdtemplatelayoutcell hit cache 0 4 278 5 fdtemplatelayoutcell hit cache 0 5 156 fdtemplatelayoutcell hit cache 0 6 165 about self satisfied cell a fully self satisfied cell is constrainted by auto layout and each edge top left bottom right has at least one layout constraint against it its the same concept introduced as self sizing cell in ios8 using auto layout a bad one missing right and bottom a good one notes a template layout cell is created by dequeuereusablecellwithidentifier method it means that you must have registered this cell reuse identifier by one of a prototype cell of uitableview in storyboard use registernib forcellreuseidentifier use registerclass forcellreuseidentifier 如果你在天朝 可以看这篇中文博客： http blog sunnyxx com 2015 05 17 cell height calculation installation latest version 1 6 pod search uitableview fdtemplatelayoutcell if you cannot search out the latest version try pod setup release notes we recommend to use the latest release in cocoapods 1 6 fix bug in ios 10 1 4 refactor add cachebykey mode bug fixed 1 3 frame layout mode handle cells accessory view type 1 2 precache and auto cache invalidation 1 1 height cache 1 0 basic automatically height calculation license mit