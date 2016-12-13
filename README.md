# Proyecto_Final
function varargout = esde(varargin)
% ESDE MATLAB code for esde.fig
%      ESDE, by itself, creates a new ESDE or raises the existing
%      singleton*.
%
%      H = ESDE returns the handle to a new ESDE or the handle to
%      the existing singleton*.
%
%      ESDE('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in ESDE.M with the given input arguments.
%
%      ESDE('Property','Value',...) creates a new ESDE or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before esde_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to esde_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help esde

% Last Modified by GUIDE v2.5 13-Dec-2016 15:55:14

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @esde_OpeningFcn, ...
                   'gui_OutputFcn',  @esde_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before esde is made visible.
function esde_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to esde (see VARARGIN)

% Choose default command line output for esde
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes esde wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = esde_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;



% --- Executes during object creation, after setting all properties.

% --- Executes on slider movement.
function slider2_Callback(hObject, eventdata, handles)

Valor=get(hObject,'value'); 
 Valor=round(Valor)
 save('Valor.mat','Valor')
 load('variables.mat')

if cc==1

 P=plot(B(Valor,1), B(Valor,2),'or','LineWidth', 4.5)
 cc=2
 save('variables.mat')
elseif cc==2;
   load('Valor.mat')

   if Valor<=13
       set(P,'Color',[1 0 0])
       
   elseif Valor<=17
       set(P,'Color',[0 1 0])
       
   elseif Valor==27
       set(P,'Color',[1 1 0])
       
   elseif Valor<=30
       set(P,'Color',[(192/255) (192/255) (192/255)])
   
   else Valor==31
       set(P,'Color',[0 0 0])
   end
   
   set(P,'XData',B(Valor+1,1))
   set(P,'YData',B(Valor+1,2))
   save('variables.mat')

 end 

    
% set(P,'XData',B(Valor+1,1))
% set(P,'YData',B(Valor+1,2))

% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'Value') returns position of slider
%        get(hObject,'Min') and get(hObject,'Max') to determine range of slider


% --- Executes during object creation, after setting all properties.

% hObject    handle to figure1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% --- Executes during object creation, after setting all properties.
function slider2_CreateFcn(hObject, eventdata, handles)
% hObject    handle to slider2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called


% Hint: slider controls usually have a light gray background.
if isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor',[.9 .9 .9]);
end




%% Hint: place code in OpeningFcn to populate axes3


% --- Executes during object creation, after setting all properties.
function axes4_CreateFcn(hObject, eventdata, handles)
% hObject    handle to axes4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called
A=xlsread('Libro1ed.xlsx');
B=[A(:,5) A(:,6)]
plot(B(:,1),B(:,2), 'LineWidth', 1.5)
xlabel('Deformación Unitaria');
ylabel('Esfuerzo Axial (lb/in^2)');
title('Esfuerzo - Deformación para Acero A512');
cc=1;
grid on
hold on

save('variables.mat')
% Hint: place code in OpeningFcn to populate axes4
