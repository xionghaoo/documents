# Android笔记

## UI相关

#### 圆形Ripple效果
> targetApi > 21, 21以下为矩形Ripple效果

方法：用AppCompact主题，给ImageButton设**android:background="?selectableItemBackgroundBorderless"**属性

效果可以在padding的范围内看到

```xml
<ImageButton
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:padding="20dp"
        android:background="?selectableItemBackgroundBorderless"
        android:src="@drawable/ic_bug_report_black_24dp"
/>
```
