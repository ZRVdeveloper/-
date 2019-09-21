unit Unit1;

{$mode objfpc}{$H+}

interface

uses
  Classes, SysUtils, FileUtil, Forms, Controls, Graphics, Dialogs, StdCtrls,
  ExtCtrls;

type

  { TForm1 }

  TForm1 = class(TForm)
    Button1: TButton;
    Button2: TButton;
    Button3: TButton;
    CheckGroup1: TCheckGroup;
    ComboBox1: TComboBox;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure Button3Click(Sender: TObject);
    procedure FormCreate(Sender: TObject);
  private
    { private declarations }
  public
    { public declarations }
  end;

var
  Form1: TForm1;
  PascalFiles: TStringList;
  str:string;

implementation

{$R *.lfm}

{ TForm1 }

procedure TForm1.FormCreate(Sender: TObject);
begin

  PascalFiles := FindAllFiles('klas\', '', true); //находим, например, все исходные файлы паскаля
  ComboBox1.Items := PascalFiles;
  PascalFiles.Free;
end;

procedure TForm1.Button2Click(Sender: TObject);
begin
  PascalFiles := FindAllFiles('klas\', '', true); //находим, например, все исходные файлы паскаля
  ShowMessage(Format('Знайдено %d класи', [PascalFiles.Count]));
  ComboBox1.Items := PascalFiles;
  PascalFiles.Free;
end;

procedure TForm1.Button3Click(Sender: TObject);
var img:TImage;
    rect:TRect;
    s:string;
begin
  if CheckGroup1.Items.Count > 0 then
  begin
       img:=TImage.Create(Form1);
       img.Width:=Form1.Width;
       img.Height:=Form1.Height;
       rect:=Form1.Canvas.ClipRect;
       img.Canvas.CopyRect(rect,Form1.Canvas,rect);
       s:= FormatDateTime('dd mmmm - hh_nn_ss', Now);
       img.Canvas.TextOut(10,35,s+' журнал.png');
       img.Picture.SaveToFile('rez\'+s+' журнал.png');
       FreeAndNil(img);
       Form1.Close;
   end;
end;

procedure TForm1.Button1Click(Sender: TObject);
var
  f:text;
  m:string;
begin
  //ShowMessage(IntToStr(ComboBox1.ItemIndex));
  CheckGroup1.Items.Clear;
  if ComboBox1.ItemIndex > -1 then
  begin
       str:= ComboBox1.Items[ComboBox1.ItemIndex] ;
      //ShowMessage(str);
      AssignFile (f,str);
       // Открыть файл для чтения
       reset(f);
       // Считываем строки, пока не закончится файл
       while not eof(f) do
        begin
          readln(f, m);
          CheckGroup1.Items.Add(m);
        end;
  end;

end;

end.

