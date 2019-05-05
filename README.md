# SimpleAdapter
# ![截图](https://github.com/JojoBiid/SimpleAdapter/blob/master/app/src/main/res/drawable/sa.png)
```
public class MainActivity extends AppCompatActivity {
    private String[] names = new String[]{"Lion","Tiger","Monkey","Dog","Cat","elephant"};
    private int[] image=new int[]{R.drawable.lion,R.drawable.tiger,R.drawable.monkey,R.drawable.dog,R.drawable.cat,R.drawable.elephant};
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        requestWindowFeature(Window.FEATURE_NO_TITLE);
        setContentView(R.layout.activity_main);//此处引用~~~~~
        final int color1=0xFFC5B5FF;
        final int color2=0xFFFFFFFF;
        //创建一个list集合，list集合的元素是Map
        List<Map<String,Object>> ListItems=new ArrayList<Map<String, Object>>();
        for (int i=0;i<names.length;i++){
            Map<String,Object> listItem=new HashMap<String,Object>();
            listItem.put("header",names[i]);
            listItem.put("images",image[i]);
            ListItems.add(listItem);//加入list集合
        }
        //创建一个SimpleAdapter
        SimpleAdapter simpleAdapter=new SimpleAdapter(this,ListItems,R.layout.simple,new String[]{"header","images"},new int[]{R.id.header,R.id.images});
        final ListView list=(ListView)findViewById(R.id.mylist);
        //为ListView设置Adapter
        list.setAdapter(simpleAdapter);
        list.setOnItemClickListener(new AdapterView.OnItemClickListener(){
            public void onItemClick(AdapterView<?> parent, View view, int position, long id){
                int flag=0;
                System.out.println(names[position]+position+"被单击");
                switch (flag){
                    case 0:
                        //view.setBackgroundColor(color1);
                        view.setSelected(true);
                        CharSequence text=names[position];
                        int duration= Toast.LENGTH_SHORT;
                        Toast toast=Toast .makeText(MainActivity.this,text,duration);
                        toast.show();
                        flag=1;
                        break;
                    case 1:
//                        view.setBackgroundColor(color2);
                        view.setSelected(false);
                        CharSequence text1=names[position];
                        int duration1= Toast.LENGTH_SHORT;
                        Toast toast1=Toast .makeText(MainActivity.this,text1,duration1);
                        toast1.show();
                        flag=0;
                        break;
                }
            }
        });
        list.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener(){
            public void onItemSelected(AdapterView<?> parent, View view, int position, long id){
                System.out.println(names[position]+"选中");
            }
            public void onNothingSelected(AdapterView<?> parent){

            }
        });
    }

}
```
