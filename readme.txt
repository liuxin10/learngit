-- Create table
create table RWD_EXT_BUSI_TYPE_CFG
(
  type_cfg_id      VARCHAR2(12) not null,
  type_id          VARCHAR2(12) not null,
  type_name        VARCHAR2(150),
  rule_type_code   VARCHAR2(100),
  rule_id          VARCHAR2(12),
  rule_name        VARCHAR2(150),
  rule_ver_id      VARCHAR2(12),
  rule_eff_time    DATE,
  rule_exp_time    DATE,
  eff_time         DATE,
  exp_time         DATE,
  ftype_id         VARCHAR2(12),
  ver_id           VARCHAR2(12),
  from_ver_id      VARCHAR2(12),
  update_time      DATE,
  update_staff_id  VARCHAR2(20),
  update_depart_id VARCHAR2(20),
  rsrv_str1        VARCHAR2(400),
  rsrv_str2        VARCHAR2(400),
  rsrv_str3        VARCHAR2(400),
  rsrv_str4        VARCHAR2(400)
)
tablespace USERS
  pctfree 10
  initrans 1
  maxtrans 255
  storage
  (
    initial 64K
    next 1M
    minextents 1
    maxextents unlimited
  );
-- Add comments to the table 
comment on table RWD_EXT_BUSI_TYPE_CFG
  is '业务分类配置表';
-- Add comments to the columns 
comment on column RWD_EXT_BUSI_TYPE_CFG.type_cfg_id
  is '序列';
comment on column RWD_EXT_BUSI_TYPE_CFG.type_id
  is '业务分类标识';
comment on column RWD_EXT_BUSI_TYPE_CFG.type_name
  is '业务分类名称';
comment on column RWD_EXT_BUSI_TYPE_CFG.rule_type_code
  is '归属业务大类';
comment on column RWD_EXT_BUSI_TYPE_CFG.rule_id
  is '适用规则ID';
comment on column RWD_EXT_BUSI_TYPE_CFG.rule_name
  is '适用规则名称';
comment on column RWD_EXT_BUSI_TYPE_CFG.rule_ver_id
  is '适用规则版本号，选取规则当前账期正在适用的版本号';
comment on column RWD_EXT_BUSI_TYPE_CFG.rule_eff_time
  is '适用规则生效时间';
comment on column RWD_EXT_BUSI_TYPE_CFG.rule_exp_time
  is '适用规则失效时间';
comment on column RWD_EXT_BUSI_TYPE_CFG.eff_time
  is '业务分类生效时间';
comment on column RWD_EXT_BUSI_TYPE_CFG.exp_time
  is '业务分类失效时间';
comment on column RWD_EXT_BUSI_TYPE_CFG.ftype_id
  is '父业务分类标识';
comment on column RWD_EXT_BUSI_TYPE_CFG.ver_id
  is '业务分类版本号，业务分类纯新增或提取新增子类时，系统分配的版本号序列';
comment on column RWD_EXT_BUSI_TYPE_CFG.from_ver_id
  is '业务分类来源版本号';
comment on column RWD_EXT_BUSI_TYPE_CFG.update_time
  is '操作时间';
comment on column RWD_EXT_BUSI_TYPE_CFG.update_staff_id
  is '操作员';
comment on column RWD_EXT_BUSI_TYPE_CFG.update_depart_id
  is '操作部门';
-- Create/Recreate primary, unique and foreign key constraints 
alter table RWD_EXT_BUSI_TYPE_CFG
  add constraint PK_TYPE_ID primary key (TYPE_ID)
  using index 
  tablespace USERS
  pctfree 10
  initrans 2
  maxtrans 255
  storage
  (
    initial 64K
    next 1M
    minextents 1
    maxextents unlimited
  );



-- Create table
create table RWD_EXT_BUSI_CFG
(
  cfg_id           VARCHAR2(12) not null,
  busi_id          VARCHAR2(12) not null,
  busi_name        VARCHAR2(400),
  type_cfg_id      VARCHAR2(12),
  eff_time         DATE,
  exp_time         DATE,
  update_time      DATE,
  update_staff_id  VARCHAR2(20),
  update_depart_id VARCHAR2(20),
  rsrv_str2        VARCHAR2(400),
  rsrv_str3        VARCHAR2(400),
  rsrv_str4        VARCHAR2(400),
  rsrv_str1        VARCHAR2(400)
)
tablespace TBS_RMR_DEF
  pctfree 10
  initrans 1
  maxtrans 255;
-- Add comments to the table 
comment on table RWD_EXT_BUSI_CFG
  is '业务因子配置';
-- Add comments to the columns 
comment on column RWD_EXT_BUSI_CFG.cfg_id
  is '序列';
comment on column RWD_EXT_BUSI_CFG.busi_id
  is '业务因子标识';
comment on column RWD_EXT_BUSI_CFG.busi_name
  is '业务因子名称';
comment on column RWD_EXT_BUSI_CFG.type_cfg_id
  is '业务分类序列（相同业务分类，版本不一样）';
comment on column RWD_EXT_BUSI_CFG.eff_time
  is '业务因子生效时间';
comment on column RWD_EXT_BUSI_CFG.exp_time
  is '业务因子失效时间';



-- Create table
create table RWD_EXT_BUSI_RELATE
(
  rel_id           NUMBER(12) not null,
  cfg_id           NUMBER(12),
  param_val_column VARCHAR2(30),
  param_name       VARCHAR2(50),
  val_isneed       VARCHAR2(10),
  val_type         VARCHAR2(20),
  val_num          NUMBER(12),
  update_staff_id  VARCHAR2(20),
  update_depart_id VARCHAR2(12),
  update_time      DATE
)
tablespace TBS_RMR_DEF
  pctfree 10
  initrans 1
  maxtrans 255;
-- Add comments to the table 
comment on table RWD_EXT_BUSI_RELATE
  is '业务因子属性配置';
-- Add comments to the columns 
comment on column RWD_EXT_BUSI_RELATE.rel_id
  is '序列';
comment on column RWD_EXT_BUSI_RELATE.cfg_id
  is '业务因子配置序列';
comment on column RWD_EXT_BUSI_RELATE.param_val_column
  is '属性对应的RWD_EXT_BUSI_PARAM_VAL表的字段';
comment on column RWD_EXT_BUSI_RELATE.param_name
  is '属性名称';
comment on column RWD_EXT_BUSI_RELATE.val_isneed
  is '是否必选，1必选';
comment on column RWD_EXT_BUSI_RELATE.val_type
  is '属性值类型';
comment on column RWD_EXT_BUSI_RELATE.val_num
  is '属性先后顺序';


-- Create table
create table RWD_EXT_BUSI_TYPE_RELATE
(
  rel_id           NUMBER(12) not null,
  cfg_type_id      NUMBER(12),
  param_val_column VARCHAR2(30),
  param_name       VARCHAR2(50),
  val_isneed       VARCHAR2(10),
  val_type         VARCHAR2(20),
  val_num          NUMBER(12),
  update_staff_id  VARCHAR2(20),
  update_depart_id VARCHAR2(12),
  update_time      DATE
)
tablespace TBS_RMR_DEF
  pctfree 10
  initrans 1
  maxtrans 255;
-- Add comments to the table 
comment on table RWD_EXT_BUSI_TYPE_RELATE
  is '结算因子和存储表的映射关系';
-- Add comments to the columns 
comment on column RWD_EXT_BUSI_TYPE_RELATE.rel_id
  is '序列';
comment on column RWD_EXT_BUSI_TYPE_RELATE.cfg_type_id
  is '业务分类配置序列';
comment on column RWD_EXT_BUSI_TYPE_RELATE.param_val_column
  is '业务因子值对应到RWD_EXT_BUSI_TYPE_PARAM_VAL表的字段';
comment on column RWD_EXT_BUSI_TYPE_RELATE.param_name
  is '业务因子名称';
comment on column RWD_EXT_BUSI_TYPE_RELATE.val_isneed
  is '是否必填';
comment on column RWD_EXT_BUSI_TYPE_RELATE.val_type
  is '业务因子值类型';
comment on column RWD_EXT_BUSI_TYPE_RELATE.val_num
  is '业务因子显示的先后顺序';



-- Create table
create table RWD_EXT_BUSI_TYPE_PARAM_VAL
(
  type_cfg_id VARCHAR2(30),
  str1        VARCHAR2(200),
  str2        VARCHAR2(200),
  str3        VARCHAR2(200),
  str4        VARCHAR2(200),
  str5        VARCHAR2(200),
  str6        VARCHAR2(200),
  str7        VARCHAR2(200),
  str8        VARCHAR2(200),
  str9        VARCHAR2(200),
  str10       VARCHAR2(200),
  str11       VARCHAR2(200),
  str12       VARCHAR2(200),
  str13       VARCHAR2(200),
  str14       VARCHAR2(200),
  str15       VARCHAR2(200),
  str16       VARCHAR2(200),
  str17       VARCHAR2(200),
  str18       VARCHAR2(200),
  str19       VARCHAR2(200),
  str20       VARCHAR2(200),
  str21       VARCHAR2(200),
  str22       VARCHAR2(200),
  str23       VARCHAR2(200),
  str24       VARCHAR2(200),
  str25       VARCHAR2(200),
  str26       VARCHAR2(200),
  str27       VARCHAR2(200),
  str28       VARCHAR2(200),
  str29       VARCHAR2(200),
  str30       VARCHAR2(200),
  str31       VARCHAR2(200),
  str32       VARCHAR2(200),
  str33       VARCHAR2(200),
  str34       VARCHAR2(200),
  str35       VARCHAR2(200),
  str36       VARCHAR2(200),
  str37       VARCHAR2(200),
  str38       VARCHAR2(200),
  str39       VARCHAR2(200),
  str40       VARCHAR2(200),
  str41       VARCHAR2(200),
  str42       VARCHAR2(200),
  str43       VARCHAR2(200),
  str44       VARCHAR2(200),
  str45       VARCHAR2(200),
  str46       VARCHAR2(200),
  str47       VARCHAR2(200),
  str48       VARCHAR2(200),
  str49       VARCHAR2(200),
  str50       VARCHAR2(200),
  str51       VARCHAR2(200),
  str52       VARCHAR2(200),
  str53       VARCHAR2(200),
  str54       VARCHAR2(200),
  str55       VARCHAR2(200),
  str56       VARCHAR2(200),
  str57       VARCHAR2(200),
  str58       VARCHAR2(200),
  str59       VARCHAR2(200),
  str60       VARCHAR2(200),
  str61       VARCHAR2(200),
  str62       VARCHAR2(200),
  str63       VARCHAR2(200),
  str64       VARCHAR2(200),
  str65       VARCHAR2(200),
  str66       VARCHAR2(200),
  str67       VARCHAR2(200),
  str68       VARCHAR2(200),
  str69       VARCHAR2(200),
  str70       VARCHAR2(200)
)
tablespace TBS_RMR_DEF
  pctfree 10
  initrans 1
  maxtrans 255;
-- Add comments to the table 
comment on table RWD_EXT_BUSI_TYPE_PARAM_VAL
  is '业务分类级别的业务因子值';
-- Add comments to the columns 
comment on column RWD_EXT_BUSI_TYPE_PARAM_VAL.type_cfg_id
  is '业务分类配置序列';



-- Create table
create table RWD_EXT_BUSI_PARAM_VAL
(
  cfg_id VARCHAR2(30),
  str1   VARCHAR2(200),
  str2   VARCHAR2(200),
  str3   VARCHAR2(200),
  str4   VARCHAR2(200),
  str5   VARCHAR2(200),
  str6   VARCHAR2(200),
  str7   VARCHAR2(200),
  str8   VARCHAR2(200),
  str9   VARCHAR2(200),
  str10  VARCHAR2(200),
  str11  VARCHAR2(200),
  str12  VARCHAR2(200),
  str13  VARCHAR2(200),
  str14  VARCHAR2(200),
  str15  VARCHAR2(200),
  str16  VARCHAR2(200),
  str17  VARCHAR2(200),
  str18  VARCHAR2(200),
  str19  VARCHAR2(200),
  str20  VARCHAR2(200),
  str21  VARCHAR2(200),
  str22  VARCHAR2(200),
  str23  VARCHAR2(200),
  str24  VARCHAR2(200),
  str25  VARCHAR2(200),
  str26  VARCHAR2(200),
  str27  VARCHAR2(200),
  str28  VARCHAR2(200),
  str29  VARCHAR2(200),
  str30  VARCHAR2(200),
  str31  VARCHAR2(200),
  str32  VARCHAR2(200),
  str33  VARCHAR2(200),
  str34  VARCHAR2(200),
  str35  VARCHAR2(200),
  str36  VARCHAR2(200),
  str37  VARCHAR2(200),
  str38  VARCHAR2(200),
  str39  VARCHAR2(200),
  str40  VARCHAR2(200),
  str41  VARCHAR2(200),
  str42  VARCHAR2(200),
  str43  VARCHAR2(200),
  str44  VARCHAR2(200),
  str45  VARCHAR2(200),
  str46  VARCHAR2(200),
  str47  VARCHAR2(200),
  str48  VARCHAR2(200),
  str49  VARCHAR2(200),
  str50  VARCHAR2(200),
  str51  VARCHAR2(200),
  str52  VARCHAR2(200),
  str53  VARCHAR2(200),
  str54  VARCHAR2(200),
  str55  VARCHAR2(200),
  str56  VARCHAR2(200),
  str57  VARCHAR2(200),
  str58  VARCHAR2(200),
  str59  VARCHAR2(200),
  str60  VARCHAR2(200),
  str61  VARCHAR2(200),
  str62  VARCHAR2(200),
  str63  VARCHAR2(200),
  str64  VARCHAR2(200),
  str65  VARCHAR2(200),
  str66  VARCHAR2(200),
  str67  VARCHAR2(200),
  str68  VARCHAR2(200),
  str69  VARCHAR2(200),
  str70  VARCHAR2(200)
)
tablespace TBS_RMR_DEF
  pctfree 10
  initrans 1
  maxtrans 255;
-- Add comments to the table 
comment on table RWD_EXT_BUSI_PARAM_VAL
  is '业务因子包含的结算因子的值';
-- Add comments to the columns 
comment on column RWD_EXT_BUSI_PARAM_VAL.cfg_id
  is '业务因子配置序列';

